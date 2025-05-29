```
project(M::OrthogonalMatrices, p, X)
project(M::Rotations, p, X)
project(M::UnitaryMatrices, p, X)
```

接線ベクトル $X ∈ 𝔽^{n×n}$ を `M` の点 `p` での接空間に直交射影し、表現者を対応するリー代数を使用するように変更します。すなわち、次のように計算します。

$$
    \operatorname{proj}_p(X) = \frac{p^{\mathrm{H}} X - (p^{\mathrm{H}} X)^{\mathrm{H}}}{2},
$$
