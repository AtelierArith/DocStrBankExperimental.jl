```
build_bfm!(m::JuMP.AbstractModel, net::Network{SinglePhase}, ::Val{Linear})
```

`net`の値を使用して`m`に変数と制約を追加します。次の関数を呼び出します：

```julia
add_linear_variables(m, net)
add_vsqrd_variables(m, net)
add_isqrd_variables(m, net)
constrain_power_balance_with_isqrd_losses(m, net)
constrain_substation_voltage(m, net)
constrain_KVL(m, net)
constrain_cone(m, net)
```
