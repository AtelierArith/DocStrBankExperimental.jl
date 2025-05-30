```
brain_mask(mask)
```

頭蓋骨と脳と頭蓋骨の間の隙間を持つマスクから脳を抽出しようとします。

# 例

```julia-repl
julia> mask = robustmask(mag)
julia> brain = brain_mask(mask)
```

関連項目 [`robustmask`](@ref)
