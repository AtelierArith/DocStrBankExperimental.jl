DIO!(rp::RedPitaya, pin::DIOPins, val::Bool)

Set the value of DIO pin `pin` to the value `val`.

# Example

```julia
julia> DIO!(rp, DIO7_P, true)
true
```
