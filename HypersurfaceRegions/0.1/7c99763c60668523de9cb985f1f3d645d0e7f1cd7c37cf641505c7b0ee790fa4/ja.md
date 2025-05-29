```
affine_regions(f::Vector{Expression})
affine_regions(f::System)
```

アフィン超曲面のリスト 'f = [f*1,...f*k]' を入力します。超曲面配置の補集合内の領域、その符号パターン、オイラー特性、および各領域内の臨界点のインデックスを出力します。[`regions`](@ref) と同じオプションを受け付けます。

## 例

```julia
using HypersurfaceRegions
@var x y
f = [x^2 + y^2 - 1; x^2 + y^2 - 4];
affine_regions(f)
```
