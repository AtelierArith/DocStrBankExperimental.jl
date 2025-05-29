```
hermitian_structure(L::ZZLat, f::QQMatrix; check::Bool = true
                                           ambient_representation::Bool = true)
                                                                 -> HermLat
```

与えられた $\mathbb{Z}$-格 `L` と、不可約最小多項式を持つ同型 `f` に対して、`(L, f)` に関連するエルミート構造を返します。

`f` は無限の順序を持つか、少なくとも3の順序でなければなりません。この場合、格 `L` の階数は `f` の最小多項式の次数で割り切れる必要があります。

`L` が完全な階数でない場合、関連するスカラー変換のマップは `L` の有理スパン上で定義されます（[`rational_span(::ZZLat)`](@ref)を参照）。なぜなら、トレース同値に関しては格の有理スパン上での作用のみが重要だからです。`L` が完全な階数である場合、両者が同型であるため、有理スパンとしてその周囲空間を使用します（[`ambient_space(::ZZLat)`](@ref)を参照）。

`ambient_representation` が true に設定されている場合、同型 `f` は `L` の周囲空間の同型として見なされます。`check == true` の場合、関数は `L` の有理スパン上での `f` の作用の最小多項式が不可約であるかどうかをチェックします。
