DIODirection!(rp::RedPitaya, pin::DIOPins, direction::DIODirectionType)

DIOピン`pin`の方向を値`direction`に設定します。

# 例

```julia
julia> DIODirection!(rp, DIO7_P, DIO_OUT)

julia>DIODirection(rp, DIO7_P)
DIO_OUT
```
