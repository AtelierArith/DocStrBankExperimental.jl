```
build_ldf!(m::JuMP.AbstractModel, p::Inputs)
```

`p`の値を使用して`m`に変数と制約を追加します。次の関数を呼び出します：

```julia
add_variables(m, p)
constrain_power_balance(m, p)
constrain_substation_voltage(m, p)
constrain_KVL(m, p)
constrain_loads(m, p)
```
