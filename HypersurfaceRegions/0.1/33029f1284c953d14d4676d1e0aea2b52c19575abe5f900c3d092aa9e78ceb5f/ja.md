```
projective_regions(C::RegionsResult)
```

プロジェクティブ空間で融合された `C` の領域を含むベクトルのベクトルを返します。

以下のコードは、`Region` 型のベクトルのベクトルを返します：

```julia
using HypersurfaceRegions
@var x y
f = [x^2 + y^2 - 1; x^2 + y^2 - 4];
C = regions(f)
p = projective_regions(C)
```
