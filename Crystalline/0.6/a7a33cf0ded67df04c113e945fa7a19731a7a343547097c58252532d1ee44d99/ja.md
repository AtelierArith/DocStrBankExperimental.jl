```
SymmetryVector(
    nv :: AbstractVector{<:Integer},
    irlabs_nv :: AbstractVector{<:AbstractString},
    lgirsd :: AbstractDict{String, <:AbstractVector{LGIrrep{D}}}) --> SymmetryVector{D}
```

"生"ベクトル `nv` の不変表現の構造化された `SymmetryVector` 表現を構築します。このベクトルの `i` 番目の要素は、ラベル `irlabs_nv[i]` の不変の重複度を示します。対応する完全な不変情報は、`irlabs_nv` のラベルと提供されたカバー不変のセット `lgirsd` の比較によって推測されます。

生のベクトル `nv` は、その最後の要素としてバンド占有数を含む必要があります。したがって、`irlabs_nv` ベクトルの長さは `length(nv)-1` でなければなりません。

`lgirsd` と (`nv`, `irlabs_nv`) の不変ラベルのソートは異なることが許可されています：これは関数の主な用途であり、異なる順序の生ベクトルと `lgirsd` の構造化された不変ストレージとの間のマッピングを行います。
