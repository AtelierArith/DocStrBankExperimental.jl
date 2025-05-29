```
cheb_series_integrate(df::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
cheb_series_integrate!(f::AbstractVector{TFC}, df::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
```

Compute the indefinite integral of a function $f'(x)$ given its Chebyshev series, with the constant of integration chosen such that $f(-1) = 0$.

# Mathematical Details

If the input function $f'(x)$ is represented by a Chebyshev series of length $n$:

$$
f'(x) = \sum_{r=0}^{n-1} c_r T_r(x)
$$

its integral $f(x)$ is represented by a Chebyshev series of length $n+1$:

$$
f(x) = \sum_{r=0}^{n} b_r T_r(x)
$$

where:

  * $$
    b_0
    $$

    is determined from the constant of integration as:

$$
b_0 = \sum_{r=1}^{n} (-1)^{r+1} b_r
$$

  * The other coefficients are given by:

$$
b_1 = c_0 - c_2/2
b_r = (c_{r-1} - c_{r+1})/(2r) \text{ for } r > 1
$$

with $c_{n+1} = c_{n+2} = 0$.

# Arguments

  * `df`: Vector of Chebyshev series coefficients of $f'$
  * `f`: Vector of Chebyshev series coefficients of $f$

# References

  * [chebfun/@chebtech/cumsum.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech/cumsum.m)
