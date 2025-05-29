DIODirection!(rp::RedPitaya, pin::DIOPins, direction::DIODirectionType)

Set the direction of DIO pin `pin` to the value `direction`.

# Example

```julia
julia> DIODirection!(rp, DIO7_P, DIO_OUT)

julia>DIODirection(rp, DIO7_P)
DIO_OUT
```
