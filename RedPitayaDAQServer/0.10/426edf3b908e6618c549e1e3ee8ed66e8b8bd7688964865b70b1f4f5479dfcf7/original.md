```
samplesPerPeriod!(rp::RedPitaya, value)
```

Set the number of samples per period.

# Example

```julia
julia> samplesPerPeriod!(rp, 256)
true

julia> samplesPerPeriod(rp)
256

```
