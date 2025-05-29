```
diff(panel::PanelStructure, v::AbstractArray; kwargs...)
```

`panel`内の各ユニットに対する観測値の`v`の差分を返します。デフォルトでは、最初の差分を計算します。 [`diff!`](@ref)も参照してください。

# キーワード

  * `order::Integer=1`: 取る差分の順序。
  * `l::Integer=1`: 各観測ペア間の時間間隔。
  * `default=missing`: 差分が存在しないインデックスのデフォルト値。
