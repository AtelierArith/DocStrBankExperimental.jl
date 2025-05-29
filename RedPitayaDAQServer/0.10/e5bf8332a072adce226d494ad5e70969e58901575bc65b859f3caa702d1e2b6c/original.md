```
counterTrigger_arm!(rp::RedPitaya, val::Bool)
```

Set whether the counter trigger is armed or not. Return `true` if the command was successful.

# Examples

```julia
julia> counterTrigger_arm!(rp, true)
true

julia> counterTrigger_isArmed(rp)
true
```
