```
GaussianBeam(q; zpos, n=1.0, λ=633e-9)
```

Returns a `GaussianBeam` defined by complex beam parameter `q`.

## Example

```jldoctest
julia> GaussianBeam(12 + 1im * 1.0 * π * 100e-6^2 / 633e-9)
GaussianBeam{Float64}(12.0 + 0.049630215696521214im, 0.0, 1.0, 6.33e-7)
```
