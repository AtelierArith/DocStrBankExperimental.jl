```
hrep(hyperplanes::HyperPlaneIt; d::FullDim)
```

リストのハイパープレーン `hyperplanes` から次元 `d` のアフィン空間を作成します。

### 例

```julia
hrep([HyperPlane([0, 1, 0], 1), HyperPlane([0, 0, 1], 0)])
```

すべての点 $(x_1, 0, 0)$ を含む1次元のアフィン部分空間を作成します。すなわち、$x_1$-軸です。

```julia
hrep([HyperPlane([1, 1], 1), HyperPlane([1, 0], 0)])
```

点 $(0, 1)$ のみを含む0次元のアフィン部分空間を作成します。
