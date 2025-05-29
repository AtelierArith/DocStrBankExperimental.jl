DIOHBridge!(rp::RedPitaya, pin::DIOPins, val::Bool)

DIOHBridgeピン`pin`の値を`val`に設定します。

# 例

```julia
julia> DIOHBridge!(rp, DIO7_P, true)
true
```
