```
vsample!(B::AbstractArray, A::AbstractArray)
```

`sample!`と同じですが、基盤となるMarsagliaサンプラーが`LoopVectorization`を使用しています。

関連情報: [`vtsample!`](@ref), [`sample!`](@ref), [`tsample!`](@ref)
