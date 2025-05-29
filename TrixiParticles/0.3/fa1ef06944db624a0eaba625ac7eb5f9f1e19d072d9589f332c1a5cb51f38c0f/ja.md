```
BoundaryModelLastiwka(; extrapolate_reference_values::Bool=false)
```

[`OpenBoundarySPHSystem`](@ref)の境界モデル。このモデルは、特性変数を使用して適切な値を出口または入口に伝播させ、Lastiwka et al. (2009)によって提案されました。特定の流れの方向を[`BoundaryZone`](@ref)に渡す必要があります。手法の詳細については、[以下の説明](@ref method_of_characteristics)を参照してください。

# キーワード

  * `extrapolate_reference_values=false`: `true`の場合、参照値は流体領域から境界粒子に外挿されます。これは、参照値が事前に知られていない開放境界に対して便利です。**注意:** この機能は実験的であり、まだ完全には検証されていません。現時点では、その使用を支持する公表された文献は認識していません。
