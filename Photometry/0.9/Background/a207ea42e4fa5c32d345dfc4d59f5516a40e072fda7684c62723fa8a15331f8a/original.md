```
BiweightScaleRMS(c=9.0, M=nothing)
```

Uses the robust biweight scale statistic for background RMS estimation.

The biweight scale is the square root of the biweight midvariance. The biweight midvariance uses a tuning constant, `c`, and an optional initial guess of the central value `M`.

$$
ζ²_{biscl} = \frac{n ∑_{|uᵢ|<1}{(xᵢ - M)²(1 - uᵢ²)⁴}}{\left[∑_{|uᵢ|<1}{(1-uᵢ²)(1-5uᵢ²)}\right]²}
$$

$$
uᵢ = \frac{(xᵢ - M)}{c⋅\mathrm{MAD}(x)}
$$

Where $\mathrm{MAD}(x)$ is median absolute deviation of `x`.

# Examples

```jldoctest
julia> data = ones(3, 5);

julia> BiweightScaleRMS()(data)
0.0

julia> BiweightScaleRMS(c=3.0)(data, dims=1)
1×5 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0
```
