```
isapprox(v1::T, v2::T, 
         [cntr::Union{Char, Nothing, AbstractMatrix{<:Real}}, modw::Bool];
         kwargs...) --> Bool
```

2つのベクトル量 `v1` と `v2` の近似等価性を計算します。型は `T = Union{<:AbstractVec, <:AbstractPoint}` です。

`modw = true` の場合、同値は格子ベクトルの剰余として考慮されます。`v1` と `v2` が非原始格子の従来の設定にある場合、関連する（原始的な）格子ベクトルが比較に使用されることを保証するために、センタリングタイプ `cntr`（[`Bravais.centering`](@ref)を参照）を指定する必要があります。

## オプション引数

  * `cntr`: 提供されない場合、比較は原始格子ベクトルによる同値を考慮しません（`cntr=nothing`を設定するのと同等です）。`v1` と `v2` の基底における格子ベクトルによる同値のみが考慮されます。`cntr` は関連する変換行列を直接与えるために `D`×`D` の `AbstractMatrix` としても提供できます。
  * `modw`: 格子ベクトルの倍数によって異なるベクトルが同値と見なされるかどうか。
  * `kwargs...`: `Base.isapprox` に転送されるオプションのキーワード引数（例: `atol` と `rtol`）。
