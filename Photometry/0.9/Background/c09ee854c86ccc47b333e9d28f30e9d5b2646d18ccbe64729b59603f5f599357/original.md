```
sigma_clip(x, sigma; fill=:clamp, center=median(x), std=std(x, corrected=false))
sigma_clip(x, sigma_low, sigma_high; fill=:clamp, center=median(x), std=std(x, corrected=false))
```

This function returns sigma-clipped values of the input `x`.

Specify the upper and lower bounds with `sigma_low` and `sigma_high`, otherwise assume they are equal. `center` and `std` are optional keyword arguments which are functions for finding central element and standard deviation.

If `fill === :clamp`, this will clamp values in `x` lower than `center - sigma_low * std` and values higher than `center + sigma_high * std`. Otherwise, they will be replaced with `fill`.

# Examples

```jldoctest
julia> x = randn(100_000);

julia> extrema(x)
(-4.496308951466683, 4.080724496910187)

julia> x_clip = sigma_clip(x, 1);

julia> extrema(x_clip) # should be close to (-1, 1)
(-1.0042721545326967, 0.9957463910682249)
```
