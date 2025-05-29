```
identify_phase(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)::Symbol
```

指定された条件 `V`、`T`、および `z` における流体の相を返します。`Clapeyron.pip` からの相識別パラメータ基準を使用します。

相が液体（または液体のような）であれば `:liquid` を返し、相が蒸気（または蒸気のような）であれば `:vapour` を返し、相識別パラメータの計算に失敗した場合は `:unknown` を返します。

内部的には、[`Clapeyron.volume`](@ref) を呼び出して `V` を取得し、`VT_enthalpy(model,V,T,z)` を介してプロパティを計算します。

キーワード `phase`、`threaded`、および `vol0` は [`Clapeyron.volume`](@ref) ソルバーに渡されます。
