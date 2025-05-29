counterTrigger_enabled!(rp::RedPitaya, val)

Set whether the counter trigger is enabled or not. Return `true` if the command was successful.

# Examples

```julia
julia> counterTrigger_enabled!(rp, true)
true

julia> counterTrigger_enabled(rp)
true
```
