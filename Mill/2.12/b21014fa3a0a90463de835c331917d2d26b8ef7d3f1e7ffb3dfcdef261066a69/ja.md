```
MaybeHotVector{T, U} <: AbstractVector{U}
```

ワンホットエンコードされた変数を表すためのベクトルのような構造。`Flux.OneHotVector`のようですが、`missing`値をサポートしています。

[`maybehot`](@ref)関数で構築します。

関連情報: [`MaybeHotMatrix`](@ref), [`maybehotbatch`](@ref).
