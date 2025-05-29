DIOHBridge!(rp::RedPitaya, pin::DIOPins, val::Bool)

Set the value of DIOHBridge pin `pin` to the value `val`.

# Example

```julia
julia> DIOHBridge!(rp, DIO7_P, true)
true
```
