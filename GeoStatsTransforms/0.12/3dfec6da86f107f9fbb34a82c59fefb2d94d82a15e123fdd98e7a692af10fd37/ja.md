```
UniqueCoords(var₁ => agg₁, var₂ => agg₂, ..., varₙ => aggₙ)
```

ユニークな座標を持つデータの位置を保持します。

変数 `varᵢ` の重複は、集約関数 `aggᵢ` で集約されます。変数 `varᵢ` に対して集約関数が定義されていない場合、デフォルトの集約関数が使用されます。デフォルトの集約関数は、連続変数の場合は `mean`、それ以外の場合は `first` です。

# 例

```julia
UniqueCoords(1 => last, 2 => maximum)
UniqueCoords(:a => first, :b => minimum)
UniqueCoords("a" => last, "b" => maximum)
```
