# Homework 4: Prediction vs Inference

#### Q1 - linear algebra practice
With the usual regression assumptions:

  - Linearity: $$Y=X\beta + \epsilon$$
  - Unbiased errors: $$E(\epsilon\mid X) = 0_{n \times 1}$$
  - I.I.D. errors: $$Cov(\epsilon\mid X) = \sigma^2 I$$
  - Let $$X$$ be $$n\times p$$, $$X_{new}$$ be $$m \times p$$
  - $$Y$$ is $$n\times 1$$ then $$Y_{new}$$ is $$m \times 1$$

Then please show

  - Unbiased prediction: $$E(\hat{Y}_{new}\mid X, X_{new}) = X_{new}\beta$$
  - Closed form variance for regression line at new locations: $$Cov(\hat{Y}_{new}\mid X, X_{new}) = \sigma^2 X_{new} (X^TX)^{-1}X_{new}^T$$
  - Closed form variance for prediction error: $$Cov(Y_{new} - \hat{Y}_{new}\mid X, X_{new}) = \sigma^2 (I_{m\times m} + X_{new} (X^TX)^{-1}X_{new}^T)$$

#### Q2 - generating your own examples
Please numerically verify the formulas based on matrices match our previous formulas for SLR (e.g. those given on the midterm) for the following quantities (hint: we've shown that `summary.lm()` agrees with our formulas before). You are expected to generate your own $$n$$, $$\beta$$, $$\epsilon$$ etc.

- $$\hat{SE}(\hat{\beta}_i\mid X)$$
- $$\hat{SE}(\hat{Y}\mid X)$$

#### Q3 - pro/con of numerical verification
Continuing from Q2, numerical verifications in general do not "prove" that the matrix formulas are correct.
What value does numerical verification provide then? Please answer as if you're explaining to a freshman why we bother with numerical verfications?

#### Q4 - confidence intervals from different bootstraps
Use the file `hw4_scatter.csv` on Canvas, please reproduce the following plot:
<img src="../images/hw4_conf_inter_boot.png" alt="conf_inter_boot" width='600'>

#### Q5 - intuition practice
- Continuing from Q4, If we used `predict.lm(..., interval="confidence")`, would its results align better with the classic bootstrap or bootstrapping the residuals?
- Which method is more "correct", the classic bootstrap or bootstrapping the residuals?

#### Q6 - Prediction Intervals
First generate your data following the process below:

```r
set.seed(100)
n <- 50
x_range <- 1:20
beta0 <- -5
beta1 <- 1.2
x <- sample(x_range, n, replace=TRUE)
y <- beta0 + beta1 * x + rnorm(n)
```
For the first 3 problems, do not overwrite your original `x`, `y` data pairs.
- Plot the `80%` confidence interval and prediction interval on the scatter plot of x and y (hint: `predict.lm()`). The range of x values should be all the integers from 1 through 20.
- Generate `1000` new data pairs, what percentage of them are within your prediction interval?


#### Q7 - Prediction or inference
For each of the following, please state whether we should care about the prediction interval or the confidence interval for the regression line, no need for explanation.
- You have data between engagement with similar startups (e.g. page views) and marketing spend from multiple companies, you're curious about how much engagement your startup will get if you spend X dollars. Should you use a prediction interval or confidence interval?
- You have data on a specific spring between the weight placed on it vs the length it stretched (the length is measured by eye-balling, i.e. noisy). You want to guess the length of this particular spring if you give it weights you have not measured before, should you compute the confidence interval or the prediction interval for this problem?
- The government wants to learn about the relationship between investment in education vs poverty levels to make policies that would affect many households, should they compute the confidence interval or the prediction interval?


{% include lib/mathjax.html %}
