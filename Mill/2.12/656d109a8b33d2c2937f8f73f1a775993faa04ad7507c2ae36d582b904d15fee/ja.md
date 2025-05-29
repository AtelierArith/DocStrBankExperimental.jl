```
MaybeHotMatrix{T, V} <: AbstractMatrix{U}
```

一つのホットエンコードされた変数を表現するための行列のような構造。`Flux.OneHotMatrix`のようですが、`missing`値をサポートしています。

[`maybehotbatch`](@ref)関数で構築します。

関連情報: [`MaybeHotVector`](@ref), [`maybehot`](@ref).
