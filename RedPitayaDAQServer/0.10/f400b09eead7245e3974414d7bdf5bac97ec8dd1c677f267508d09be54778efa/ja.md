DIODirection(rp::RedPitaya, pin::DIOPins)

DIOピン`pin`の方向を取得します。

# 例

```julia
julia> DIODirection!(rp, DIO7_P, DIO_OUT)

julia>DIODirection(rp, DIO7_P)
DIO_OUT
```
