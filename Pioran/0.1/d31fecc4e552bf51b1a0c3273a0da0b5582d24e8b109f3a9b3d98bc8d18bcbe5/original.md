```
 Celerite(a, b, c, d)
```

Celerite covariance Function

  * `a`: the amplitude of the first term
  * `b`: the amplitude of the second term
  * `c`: the decay rate of the covariance function
  * `d`: the `period` of the covariance function

$$
k(τ) = \exp(-c τ) (a \cos(d τ) + b \sin(d τ))
$$

See [Foreman-Mackey et al. (2017)](https://ui.adsabs.harvard.edu/abs/2017AJ....154..220F) for more details.
