<br />
<p align="center">
  <a href="https://smmehrab.github.io/chatAppUI/">
    <img src="assets/Stanford_Logo.jpeg" alt="Logo" width="200" height="200">
  </a>

  <h1 align ="center">Machine Learning</h1>

  <p align="center">
    Notes taken, while going through the following course on Coursera:
   <br />
   <br />
	   <a href="https://www.coursera.org/learn/machine-learning">
            <strong>Explore the course »</strong>
       </a>
   <br />
   <br />
 </p>
</p>
<br />


# Introduction

<br/>

## Applications

- Data mining
    -  Large datasets from growth of automation/web. 
        <br/>
        For example, web click data, medical records, computational biology, engineering etc.

- Applications that we can't program by hand.
    - Autonomous helicopter, handwriting recognition, most of NLP, computer vision etc.

- Self-customizing programs
    - Amazon, Netflix product recommendations etc.

- Understanding human learning (brain, real AI)

<br/>

## What is Machine Learning?

- Field of study that gives computers the ability to learn without being explicitly programmed. (Arther Samuel, 1959)

- Well-posed Learning Problem: <br/>
  A computer program is said to learn from **experience E** with respect to some **task T** and some **performance measure P**, if its performance on **T**, as measure by **P**, improves with experience **E**. <br/>
  > "Experience Makes A Program Wiser"

<br/>

## Types of Algorithms

- Supervised Learning

- Unsupervised Learning

> **Others:** Reinforcement learning, recommender systems etc.

<br/>

## Supervised Learning

**Labeled Dataset**, some correct answers are given on the dataset.

### Housing Price Prediction

(Regression Algorithm - predicting continuous valued output)

<img src="assets/1HousingPricePrediction.jpg">

We can draw a straight line through the cross points (Or known data) and predict our price for a 750 feet<sup>2</sup> house from that straight line.

However, we will get more accurate result if we draw a quadric function through the known dataset instead of just drawing a straight line. 

>Picking, which function define the dataset more accurately, is our choice.

### Breast Cancer Classification (Malignant, Benign)

(Classification Algorithm - predicting discrete valued output)

<img src="assets/2BreastCancerClassification1.jpg">

Trying to predict if a tumor is malignant/benign from its size, when the dataset contains the correct answers for some of the tumor sizes. (Based on 1 feature only)

<img src="assets/2BreastCancerClassification2.jpg">

Trying to predict if a certain aged patient has a malignant/benign tumor, when the dataset contains the correct answers for some (patient age, tumor size) pairs. (Based on 2 features)

>Interestingly, we have some algorithms, which can learn from infinite number of features. 

>But how do we even store an infinite number of things in the computer when its memory capacity is limited. It turns out that when we talk about an algorithm called the Support Vector Machine, it has a neat mathematical trick that allows a computer to deal with an infinite number of features.

<br/>

## Unsupervised Learning

**Non-labeled Dataset**, no label (correct/wrong) is given on the dataset. We will have to find some structure on the given data. 

> The algorithm will not try to provide any labeled output here. It will just try to find the similarity among some of the data via finding some structure on the dataset.

> For example, market segmentation, social network analysis, astronomical data analysis etc.

### Clustering Algorithm

<img src="assets/3ClusteringAlgorithm.jpg">

>One application of this, is on Google News. 
  
>Every day hundreds of thousands news stories are published, and google news groups them into cohesive news stories.

### Cocktail Party Algorithm

Suppose, we are in a cocktail party, where two of our friends, Mamun & Shuvo are giving speech at the same time yet in two different corners of the room. And we have two microphones on the room, at different relative (random) distances from Alice & Bob.

So, naturally, each microphone will record a different combination of their voices. Maybe Mamun's voice will seem louder on microphone1 and maybe Shuvo's voice will seem louder on microphone2. But each microphone would cause an overlapping combination of both of their voices.

What we can do is, give these two recordings as input to the cocktail party algorithm. 

The algorithm will then try to find a similar structure on the dataset, which is trying to distinguish the similar voice in this case and separate the two recordings. 

<br/>
<br/>

# Univariate Linear Regression

This simply, linear regression with one variable feature. 

As you already know, in supervise learning, we have a dataset (also known as training set). Our job is to predict output data from the training set. 

Some notations to remember:
```
m   = "count"   of training examples ((x, y) denotes one training example)
x   = "input"   variable/feature
y   = "output"  variable/feature 
```

### Model

<img src="assets/4ModelRepresentation.jpg">

- Hypothesis:  **h<sub>&theta;</sub>(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub> . x** <br/>
  
  which just represents a linear function. <br/>
  &theta;<sub>0</sub>, &theta;<sub>1</sub> = parameters

We get to choose the parameters, or indirectly changing the
hypothesis function according to our need. 
  
We choose the parameters so that the hypothesis function provides
result as close to y as it's possible, for the training examples (x, y). In other words, generating a function, which when plotted on the graph, almost represents the dataset as closely as possible.

### Cost Function

-  minimize &theta;<sub>0</sub>, &theta;<sub>1</sub> : J(&theta;<sub>0</sub>, &theta;<sub>1</sub>)<br/>
  
    Cost Function, **J(&theta;<sub>0</sub>, &theta;<sub>1</sub>) = (1/2*m) * &sum; ( h<sub>&theta;</sub>(x<sub>i</sub>) - y<sub>i</sub> )<sup>2</sup>**<br/>
    
    where 1 <= i <= m (number of training examples)

> This Cost Function is also called a Square Error Function.

<img src="assets/5CostFunction1.jpg">

<img src="assets/5CostFunction2.jpg">

Each combination of the parameters will not only give us a value of the hypothesis function, but also it will provide us with a value of the cost function too. And if we try enough combinations of the parameters we can plot the cost function's values on graph and get a graphical representation for the cost function. 

Then, from that graphical representation, we can easily acquire the point that minimizes the cost function, which indeed represents our desired combination of parameters. 
  
  For 1 parameter,

  <img src="assets/5CostFunction3.jpg">

  For 2 parameters,

  <img src="assets/5CostFunction4.jpg">

  <img src="assets/5CostFunction5.jpg">

### Gradient Descent Algorithm

- Start with some combination of the parameters ( &theta;<sub>0</sub>, &theta;<sub>1</sub> )

- Keep changing to reduce J( &theta;<sub>0</sub>, &theta;<sub>1</sub> ) until we hopefully end up at a minimum

<img src="assets/6GradientDescent1.jpg">

- &alpha; = learning rate, how big a step you are taking while going downhill.

- derivative term = slope of the function on point ( &theta;<sub>0</sub>, &theta;<sub>1</sub> ).

<img src="assets/6GradientDescent2.jpg">

> The cost function of linear regression will always be a convex function (a bowl-shaped function). So, the fact that, different initial point can lead us into different local minimum point, will not bother us. As the bowl-shaped function will only have one minimum local point. 

> The algorithm that we just went over, is sometimes also called "Batch" Gradient Descent. (Each step of gradient descent uses all the training examples)

<br/>

# Multivariate Linear Regression

Now, the nummber of input variable features will be at least more than one. 

<img src="assets/7MultivariateLinearRegression3.jpg">

<img src="assets/7MultivariateLinearRegression1.jpg">

<img src="assets/7MultivariateLinearRegression2.jpg">

<img src="assets/7MultivariateLinearRegression4.jpg">

<img src="assets/7MultivariateLinearRegression5.jpg">

<img src="assets/7MultivariateLinearRegression6.jpg">

<img src="assets/7MultivariateLinearRegression7.jpg">

<img src="assets/7MultivariateLinearRegression8.jpg">

<img src="assets/7MultivariateLinearRegression9.jpg">

<br/>

# Octave/Matlab Tutorial

- https://www.gnu.org/software/octave/
- <a href="others/octave.pdf">octave.pdf</a>
- <a href="others/rob2-03-octave.pdf">rob2-03-octave.pdf</a>

<br/>

# Logistic Regression

# Regularization

# Neural Networks: Representation

# Neural Networks: Learning

