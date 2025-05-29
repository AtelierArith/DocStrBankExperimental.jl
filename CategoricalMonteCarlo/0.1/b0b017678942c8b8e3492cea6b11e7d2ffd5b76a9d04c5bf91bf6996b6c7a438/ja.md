```
vsample(::Type{T<:Real}=Int, A::AbstractArray, n_sim::Int; [dims=:], [n_cat=nothing])
```

完全なドキュメントについては `sample` を参照してください。動作は同じですが、基盤となるMarsagliaサンプラーは `LoopVectorization` を使用しています。時々、しかし常にではなく、速度向上をもたらします。

関連情報: [`vtsample`](@ref), [`sample`](@ref), [`tsample`](@ref)
