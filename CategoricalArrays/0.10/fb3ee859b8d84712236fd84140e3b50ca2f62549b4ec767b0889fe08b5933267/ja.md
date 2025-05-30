```
levels!(A::CategoricalArray, newlevels::Vector; allowmissing::Bool=false)
```

カテゴリカル配列 `A` のレベルを設定します。レベルの出現順序は [`levels`](@ref DataAPI.levels) によって尊重され、これによりいくつかの操作で結果の表示に影響を与える可能性があります。もし `A` が順序付きである場合（[`isordered`](@ref) を参照）、`<`、`>` および類似の演算子を使用した順序比較にも使用されます。レベルの再順序付けは、配列内のエントリの値に影響を与えることはありません。

もし `A` が欠損値を受け入れる場合（すなわち `eltype(A) >: Missing`）で、`allowmissing=true` の場合、除外されたレベルに対応するエントリは `missing` に設定されます。そうでない場合、`newlevels` はデータに現れるすべてのレベルを含む必要があります。
