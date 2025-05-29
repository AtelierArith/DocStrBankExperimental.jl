```
BernoulliLogit(logitp=0.0)
```

A *Bernoulli distribution* that is parameterized by the logit `logitp = logit(p) = log(p/(1-p))` of its success rate `p`.

$$
P(X = k) = \begin{cases}
\operatorname{logistic}(-logitp) = \frac{1}{1 + \exp{(logitp)}} & \quad \text{for } k = 0, \\
\operatorname{logistic}(logitp) = \frac{1}{1 + \exp{(-logitp)}} & \quad \text{for } k = 1.
\end{cases}
$$

External links:

  * [Bernoulli distribution on Wikipedia](http://en.wikipedia.org/wiki/Bernoulli_distribution)

See also [`Bernoulli`](@ref)
