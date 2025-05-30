```
robustmask(weight::AbstractArray; factor=1, threshold=nothing)
```

強度/重み画像からマスクを作成し、しきい値を推定して穴を埋めます。少なくとも1つの隅が信号なしでノイズのみを含むと仮定します。自動しきい値は`factor`で乗算されます。

# 例

```julia-repl
julia> mask1 = robustmask(mag); # 大きさを使用
julia> mask2 = phase_based_mask(phase); # 位相を使用
julia> mask3 = robustmask(romeovoxelquality(phase; mag)); # 大きさと位相を使用
julia> brain = brain_mask(robustmask(romeovoxelquality(phase; mag); threshold=0.9));
```

参照: [`brain_mask`](@ref)
