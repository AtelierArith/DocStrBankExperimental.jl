```
geodesic(Y::Manifold, Δ)
```

入力として多様体 `Y` の要素と、対応する接空間の中の接ベクトル `Δ` を取り、測地線（指数写像）を計算します。

異なる表記法では、入力として $\mathcal{M}$ の要素 $x$ と $T_x\mathcal{M}$ の要素を取り、$\mathtt{geodesic}(x, v_x) = \exp(v_x)$ を返します。

# 例

```jldoctest
using GeometricMachineLearning

Y = StiefelManifold([1. 0. 0.;]' |> Matrix)
Δ = [0. .5 0.;]' |> Matrix
Y₂ = geodesic(Y, Δ)

Y₂' * Y₂ ≈ [1.;]

# 出力

true
```

# 実装

内部的にこの `geodesic` メソッドは [`geodesic(::StiefelLieAlgHorMatrix)`](@ref) を呼び出します。
