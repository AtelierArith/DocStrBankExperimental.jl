```
tsample!(B::AbstractArray, A::AbstractArray; [chunksize=5000])
```

`sample!`と同じですが、スレッドベースの並列処理を使用して計算を加速します。また、基盤となるMarsagliaサンプラーは`LoopVectorization`を使用しています。

関連情報: [`vsample!`](@ref), [`sample!`](@ref), [`tsample!`](@ref)
