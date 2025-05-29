```
vtrmse(x::AbstractArray, y::AbstractArray; dims=:)
```

次元 `dims` に沿ったスライスに対応するベクトル間の平均二乗誤差の平方根を計算します。`sqrt.(vmse(...))` よりも効率的で、`sqrt` 操作が生成時に行われるため、そうでなければ発生する完全なトラバースを排除します。スレッド対応。

関連情報: [`vtmse`](@ref)
