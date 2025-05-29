```
hermitian_structure_with_transfer_data(L::ZZLat, f::QQMatrix; check::Bool = true,
                                                              ambient_representation::Bool = true)
                                                                          -> HermLat, AbstractSpaceRes
```

与えられた $\mathbb{Z}$-格 `L` と、既約最小多項式を持つ同型 `f` に対して、`(L, f)` に関連するエルミート構造とスカラーの変化のマップを返します。

`f` は無限の順序または少なくとも3の順序である必要があります。この場合、格 `L` のランクは `f` の最小多項式の次数で割り切れる必要があります。

`L` がフルランクでない場合、関連するスカラーの変化のマップは `L` の有理スパン上で定義されます（参照: [`rational_span(::ZZLat)`](@ref)）。なぜなら、トレース同値に関しては格の有理スパン上での作用のみが重要だからです。`L` がフルランクの場合、両者が同型であるため、有理スパンとしてその周囲空間を使用します（参照: [`ambient_space(::ZZLat)`](@ref)）。

`ambient_representation` が true に設定されている場合、同型 `f` は `L` の周囲空間の同型として見なされます。`check == true` の場合、関数は `L` の有理スパン上での `f` の作用の最小多項式が既約であるかどうかをチェックします。
