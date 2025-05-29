```julia
integrate!(
    integral4items::AbstractArray{T},
    grid::ExtendableGrids.ExtendableGrid{Tv, Ti},
    AT::Type{<:ExtendableGrids.AssemblyType},
    integrand;
    offset,
    bonus_quadorder,
    quadorder,
    regions,
    time,
    items,
    force_quadrature_rule,
    kwargs...
)

```

積分関数の署名

```
integrand!(result, qpinfo)
```

を持つ関数をグリッドのエンティティATに対して積分します。すべてのアイテムに対する結果はintegral4itemsに書き込まれます（少なくともサイズはnitems x resultの長さ）。通常通り、qpinfoは現在の数値点での情報にアクセスするために使用されます。

キーワード引数:

  * quadorder = 数値積分の次数を指定します（デフォルト = 0）
  * regions = これらの領域に積分を制限します（デフォルト = [] はすべての領域を意味します）
  * items = これらのアイテム番号に積分を制限します（デフォルト = [] はすべてのアイテムを意味します）
  * time = qpinfoに渡す時間を設定します（デフォルト = 0）
  * params = qpinfoに渡すparams配列を設定します（デフォルト = []）
  * offset = 結果配列integral4itemsに書き込むためのオフセット（デフォルト = [0]）、
