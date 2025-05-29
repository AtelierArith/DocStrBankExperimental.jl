```
JohnsonSU(ξ, λ, γ, δ)
```

The Johnson's $S_U$-distribution with parameters ξ, λ, γ and δ is a transformation of the normal distribution:

If

$$
X = \lambda\sinh\Bigg( \frac{Z - \gamma}{\delta} \Bigg) + \xi
$$

where $Z \sim \mathcal{N}(0,1)$, then $X \sim \operatorname{Johnson}(\xi, \lambda, \gamma, \delta)$.

```julia
JohnsonSU()           # Equivalent to JohnsonSU(0, 1, 0, 1)
JohnsonSU(ξ, λ, γ, δ) # JohnsonSU's S_U-distribution with parameters ξ, λ, γ and δ

params(d)           # Get the parameters, i.e. (ξ, λ, γ, δ)
shape(d)            # Get the shape parameter, i.e. ξ
scale(d)            # Get the scale parameter, i.e. λ
```

External links

  * [Johnson's $S_U$-distribution on Wikipedia](http://en.wikipedia.org/wiki/Johnson%27s_SU-distribution)
