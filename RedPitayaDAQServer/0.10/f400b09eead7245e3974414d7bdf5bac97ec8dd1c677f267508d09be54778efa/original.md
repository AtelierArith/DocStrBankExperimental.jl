DIODirection(rp::RedPitaya, pin::DIOPins)

Get the direction of DIO pin `pin`.

# Example

```julia
julia> DIODirection!(rp, DIO7_P, DIO_OUT)

julia>DIODirection(rp, DIO7_P)
DIO_OUT
```
