```
smoothed(m::AbstractModel, σ::Number)
```

モデル `m` を標準偏差 `σ` のガウスカーネルで平滑化します。

# 注意事項

これは [`convolved`](@ref) を使用してモデルを作成します。すなわち、

```julia-repl
julia> convolved(m1, m2) == smoothed(m1, 1.0)
m1 = Disk()
```
