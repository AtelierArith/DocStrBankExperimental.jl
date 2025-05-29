```
GTBasis{T, D, BN, BFT<:GTBasisFuncs{T, D, 1}} <: BasisSetData{T, D, BFT}
```

基底セット情報のコンテナ。

≡≡≡ フィールド ≡≡≡

`basis::Vector{BFT}`: 基底セットのサイズはデフォルトで `BN` に等しく保存されます（基底セットの削除や追加が行われていないと仮定）。

`S::Matrix{T}`: 重なり行列。

`Te::Matrix{T}`: 電子コアハミルトニアンの運動エネルギー部分。

`eeI::Array{T, 4}`: 電子-電子相互作用。

≡≡≡ 初期化メソッド ≡≡≡

```
GTBasis(basis::Union{Tuple{Vararg{GTBasisFuncs{T, D}}}, 
                     AbstractVector{<:GTBasisFuncs{T, D}}}) where {T, D} -> 
GTBasis{T, D}
```

基底セットを与えて `GTBasis` を構築します。
