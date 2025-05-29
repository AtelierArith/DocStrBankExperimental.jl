```
cayley(Y::Manifold, Δ)
```

入力として、マンifold `Y` の要素と、対応する接空間の中の接ベクトル `Δ` を取り、Cayleyリトラクションを計算します。

異なる表記法では、入力として $\mathcal{M}$ の要素 $x$ と $T_x\mathcal{M}$ の要素を取り、$\mathrm{Cayley}(v_x)$ を返します。

# 例

```jldoctest
using GeometricMachineLearning

Y = StiefelManifold([1. 0. 0.;]' |> Matrix)
Δ = [0. .5 0.;]' |> Matrix
Y₂ = cayley(Y, Δ)

Y₂' * Y₂ ≈ [1.;]

# 出力

true
```

[`geodesic(::Manifold{T}, ::AbstractMatrix{T}) where T`] の例を参照してください。
