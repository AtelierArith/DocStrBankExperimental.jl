```
vvmapreduce(f, op, init, A::AbstractArray, dims=:)
```

関数 `f` を配列 `A` の各要素に適用し、次に二項関数 `op` を使用して次元 `dims` にわたって結果を縮約します。縮約には初期値 `init` が必要で、これは `<:Number` であるか、単一の型引数を受け取る関数（例: `zero`）である可能性があります。`init` は二項演算子 `+`、`*`、`min`、および `max` に対してはオプションです。`dims` は `::Int`、`::NTuple{M, Int} where {M}` または `::Colon` である可能性があります。

参照: [`vvsum`](@ref), [`vvprod`](@ref), [`vvminimum`](@ref), [`vvmaximum`](@ref)
