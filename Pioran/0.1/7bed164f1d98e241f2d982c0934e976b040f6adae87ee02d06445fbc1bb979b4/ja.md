```
posterior(f::ScalableGP, y::AbstractVecOrMat{<:Real})
```

GP `f` とデータ `y` に基づいて、後方ガウス過程 `fp` を計算します。
