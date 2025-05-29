```
slowDACClockDivider!(rp::RedPitaya, val::Int32)
```

Set the clock divider of the slow DAC.

# Example

```julia
julia> slowDACClockDivider!(rp, 8)

julia>slowDACClockDivider(rp)
8
```
