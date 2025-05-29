```
Chi(ν)
```

The *Chi distribution* `ν` degrees of freedom has probability density function

$$
f(x; \nu) = \frac{1}{\Gamma(\nu/2)} 2^{1 - \nu/2} x^{\nu-1} e^{-x^2/2}, \quad x > 0
$$

It is the distribution of the square-root of a [`Chisq`](@ref) variate.

```julia
Chi(ν)       # Chi distribution with ν degrees of freedom

params(d)    # Get the parameters, i.e. (ν,)
dof(d)       # Get the degrees of freedom, i.e. ν
```

External links

  * [Chi distribution on Wikipedia](http://en.wikipedia.org/wiki/Chi_distribution)
