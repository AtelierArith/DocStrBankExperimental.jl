```
reference_chemical_potential(model::EoSModel,p,T,reference; phase=:unknown, threaded=true, vol0=nothing)
```

参照化学ポテンシャルを返します。`activity`および`activity_coefficient`の計算に使用されます。利用可能な参照は2つあります：

  * `:pure`: 参照ポテンシャルは、指定された`T`、`p`および`phase`の純成分です。
  * `:aqueous`: 指定された`T`、`p`および`phase`の純成分の化学ポテンシャルです。
  * `:sat_pure_T`: 参照ポテンシャルは、指定された`T`の純飽和液相です。
  * `:zero`: 参照ポテンシャルは、すべての成分に対してゼロに等しいです（`ActivityModel`に使用されます）。

キーワード`phase`、`threaded`および`vol0`は[`Clapeyron.volume`](@ref)ソルバーに渡されます。
