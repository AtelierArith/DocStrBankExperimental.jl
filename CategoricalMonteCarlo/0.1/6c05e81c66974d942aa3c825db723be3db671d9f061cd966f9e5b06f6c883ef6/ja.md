```
tsample!(B::AbstractArray, A::AbstractArray; [chunksize=5000])
```

`sample!`と同じですが、スレッドベースの並列処理を使用して計算を加速します。

関連情報: [`sample!`](@ref), [`vsample!`](@ref), [`vtsample!`](@ref)
