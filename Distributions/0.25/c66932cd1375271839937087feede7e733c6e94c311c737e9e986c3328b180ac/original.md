```
TDist(ν)
```

The *Students T distribution* with `ν` degrees of freedom has probability density function

$$
f(x; \nu) = \frac{1}{\sqrt{\nu} B(1/2, \nu/2)}
\left( 1 + \frac{x^2}{\nu} \right)^{-\frac{\nu + 1}{2}}
$$

```julia
TDist(d)      # t-distribution with ν degrees of freedom

params(d)     # Get the parameters, i.e. (ν,)
dof(d)        # Get the degrees of freedom, i.e. ν
```

External links

[Student's T distribution on Wikipedia](https://en.wikipedia.org/wiki/Student%27s_t-distribution)
