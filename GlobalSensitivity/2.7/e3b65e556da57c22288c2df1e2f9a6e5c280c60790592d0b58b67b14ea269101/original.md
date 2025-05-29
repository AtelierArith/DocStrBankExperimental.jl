```
RegressionGSA(; rank::Bool = false)
```

  * `rank::Bool = false`: Flag determining whether to also run a rank regression analysis

Providing this to `gsa` results in a calculation of the following statistics, provided as a `RegressionGSAResult`. If the function `f` to be analyzed is of dimensionality $f: R^n -> R^m$, then these coefficients are returned as a matrix, with the corresponding statistic in the `(i, j)`` entry.

  * `pearson`: This is equivalent to the correlation coefficient matrix between input and output. The rank version is known as the Spearman coefficient.
  * `standard_regression`: Standard regression coefficients, also known as sigma-normalized derivatives
  * `partial_correlation`: Partial correlation coefficients, related to the precision matrix and a measure of the correlation of linear models of the

## Method Details

It is possible to fit a linear model explaining the behavior of Y given the values of X, provided that the sample size n is sufficiently large (at least n > d).

The measures provided for this analysis by us in GlobalSensitivity.jl are

a) Pearson Correlation Coefficient:

$$
r = \frac{\sum_{i=1}^{n} (x_i - \overline{x})(y_i - \overline{y})}{\sqrt{\sum_{i=1}^{n} (x_i - \overline{x})^2(y_i - \overline{y})^2}}
$$

b) Standard Regression Coefficient (SRC):

$$
SRC_j = \beta_{j} \sqrt{\frac{Var(X_j)}{Var(Y)}}
$$

where $\beta_j$ is the linear regression coefficient associated to $X\_j$. This is also known as a sigma-normalized derivative.

c) Partial Correlation Coefficient (PCC):

$$
PCC_j = \rho(X_j - \hat{X_{-j}},Y_j - \hat{Y_{-j}})
$$

where $\hat{X_{-j}}$ is the prediction of the linear model, expressing $X_{j}$ with respect to the other inputs and $\hat{Y_{-j}}$ is the prediction of the linear model where $X_j$ is absent. PCC measures the sensitivity of $Y$ to $X_j$ when the effects of the other inputs have been canceled.

If `rank` is set to `true`, then the rank coefficients are also calculated.

## API

```
gsa(f, method::RegressionGSA, p_range::AbstractVector; samples::Int, batch = false)
gsa(X, Y, method::RegressionGSA)
```

### Example

```julia
using GlobalSensitivity

function linear_batch(X)
    A= 7
    B= 0.1
    @. A*X[1,:]+B*X[2,:]
end
function linear(X)
    A= 7
    B= 0.1
    A*X[1]+B*X[2]
end

p_range = [[-1, 1], [-1, 1]]
reg = gsa(linear_batch, RegressionGSA(), p_range; batch = true)

reg = gsa(linear, RegressionGSA(), p_range; batch = false)
reg = gsa(linear, RegressionGSA(true), p_range; batch = false) #with rank coefficients

X = QuasiMonteCarlo.sample(1000, [-1, -1], [1, 1], QuasiMonteCarlo.SobolSample())
Y = reshape(linear.([X[:, i] for i in 1:1000]), 1, 1000)
reg_mat = gsa(X, Y, RegressionGSA(true))
```
