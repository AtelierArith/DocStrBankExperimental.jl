```
fundamental_derivative_of_gas_dynamics(model::EoSModel, p, T, z=SA[1.]; phase=:gas, threaded=true, vol0=nothing)::Symbol
```

ガス動力学の基本的な導関数を計算します。

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_enthalpy(model,V,T,z)`を介して特性を計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
