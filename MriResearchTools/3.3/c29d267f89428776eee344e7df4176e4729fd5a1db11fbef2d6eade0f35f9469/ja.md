```
mask_from_voxelquality(qmap::AbstractArray, threshold=:auto)
```

品質マップからマスクを作成します。別のオプションは `robustmask(qmap)` を使用することです。

# 例

```julia-repl
julia> qmap = romeovoxelquality(phase_3echo; TEs=[1,2,3]);
julia> mask = mask_from_voxelquality(qmap);
```

他にも [`robustmask`](@ref)、[`brain_mask`](@ref) を参照してください。
