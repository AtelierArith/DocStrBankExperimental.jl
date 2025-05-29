```
slowDAC!(rp::RedPitaya, channel::Int64, val::Int64)
```

Set the value of the slow DAC channel `channel` to the value `val`. Return `true` if the command was successful.

# Example

```julia
julia> slowDAC!(rp, 1, 500)
true
```
