```
Ebrahimi <: DifferentialInfoEstimator
Ebrahimi(definition = Shannon(); m::Int = 1)
```

The `Ebrahimi` estimator computes the [`Shannon`](@ref) [`information`](@ref) of a timeseries using the method from [Ebrahimi1994](@citet), with logarithms to the `base` specified in `definition`.

The `Ebrahimi` estimator belongs to a class of differential entropy estimators based on [order statistics](https://en.wikipedia.org/wiki/Order_statistic). It only works for *timeseries* input.

## Description

Assume we have samples $\bar{X} = \{x_1, x_2, \ldots, x_N \}$ from a continuous random variable $X \in \mathbb{R}$ with support $\mathcal{X}$ and density function$f : \mathbb{R} \to \mathbb{R}$. `Ebrahimi` estimates the [`Shannon`](@ref) differential entropy

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

However, instead of estimating the above integral directly, it makes use of the equivalent integral, where $F$ is the distribution function for $X$,

$$
H(X) = \int_0^1 \log \left(\dfrac{d}{dp}F^{-1}(p) \right) dp
$$

This integral is approximated by first computing the [order statistics](https://en.wikipedia.org/wiki/Order_statistic) of $\bar{X}$ (the input timeseries), i.e. $x_{(1)} \leq x_{(2)} \leq \cdots \leq x_{(n)}$. The `Ebrahimi` [`Shannon`](@ref) differential entropy estimate is then

$$
\hat{H}_{E}(\bar{X}, m) =
\dfrac{1}{n} \sum_{i = 1}^n \log
\left[ \dfrac{n}{c_i m} (\bar{X}_{(i+m)} - \bar{X}_{(i-m)}) \right],
$$

where

$$
c_i =
\begin{cases}
    1 + \frac{i - 1}{m}, & 1 \geq i \geq m \\
    2,                    & m + 1 \geq i \geq n - m \\
    1 + \frac{n - i}{m} & n - m + 1 \geq i \geq n
\end{cases}.
$$

See also: [`information`](@ref), [`Correa`](@ref), [`AlizadehArghami`](@ref), [`Vasicek`](@ref), [`DifferentialInfoEstimator`](@ref).
