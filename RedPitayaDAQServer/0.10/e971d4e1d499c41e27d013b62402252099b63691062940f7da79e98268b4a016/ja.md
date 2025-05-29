DIO!(rp::RedPitaya, pin::DIOPins, val::Bool)

DIOピン`pin`の値を`val`に設定します。

# 例

```julia
julia> DIO!(rp, DIO7_P, true)
true
```
