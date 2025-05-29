```
masterTrigger!(rp::RedPitaya, val::Bool)
```

Set the master trigger of the RedPitaya to `val`. Return `true` if the command was successful.

# Example

```julia
julia> masterTrigger!(rp, true)
true

julia>masterTrigger(rp)
true
```
