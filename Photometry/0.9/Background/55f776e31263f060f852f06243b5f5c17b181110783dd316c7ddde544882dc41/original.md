```
BiweightLocationBackground(c = 6.0, M = nothing)
```

Estimate the background using the robust biweight location statistic.

$$
ξ_{biloc} = M + \frac{∑_{|uᵢ|<1}{(xᵢ - M)(1 - uᵢ²)²}}{∑_{|uᵢ|<1}{(1-uᵢ²)²}}
$$

$$
u_i = \frac{(x_i - M)}{c⋅\mathrm{MAD}(x)}
$$

Where $\mathrm{MAD}(x)$ is median absolute deviation of `x`.

# Examples

```jldoctest
julia> x = ones(3,5);

julia> BiweightLocationBackground()(x)
1.0

julia> BiweightLocationBackground(c=5.5)(x; dims = 1)
1×5 Matrix{Float64}:
 1.0  1.0  1.0  1.0  1.0
```
