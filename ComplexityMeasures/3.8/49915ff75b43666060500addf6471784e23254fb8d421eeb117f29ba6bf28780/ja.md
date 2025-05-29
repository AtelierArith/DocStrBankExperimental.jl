```
invariantmeasure(x::AbstractStateSpaceSet, binning::RectangularBinning;
    rng = Random.default_rng()) → iv::InvariantMeasure
```

データを`binning`によって決定された長方形のボックスにビニングすることに基づいて、`x`内の点に対する不変測度を推定し、その後、ビンに対する転送（ペロン-フロベニウス）演算子を近似します。転送演算子の近似から、ビンに対する不変分布を計算します。入力データは連続していると仮定します。

推定手順の詳細は、[`TransferOperator`](@ref) のドキュメントにあります。

## 例

```julia
using DynamicalSystems
henon_rule(x, p, n) = SVector{2}(1.0 - p[1]*x[1]^2 + x[2], p[2]*x[1])
henon = DeterministicIteratedMap(henon_rule, zeros(2), [1.4, 0.3])
orbit, t = trajectory(ds, 20_000; Ttr = 10)

# 軌道のいくつかの粗いグレイン化に対する不変測度を推定します。
iv = invariantmeasure(orbit, RectangularBinning(15))

# 確率とビンを取得します
invariantmeasure(iv)
```

## 確率とビン情報

```
invariantmeasure(iv::InvariantMeasure) → (ρ::Probabilities, bins::Vector{<:SVector})
```

事前に計算された不変測度から、確率と関連するビンを返します。要素`ρ[i]`は、ボックス`bins[i]`への訪問の確率です。

!!! hint "転送演算子アプローチとナイーブヒストグラムアプローチ"
    確率を得るために通常のヒストグラムを使用する代わりに、なぜ転送演算子を使うのですか？

    実際、ナイーブヒストグラムアプローチと転送演算子アプローチは、十分に長い時系列の限界において等価です（$n \to \infty$のとき）、これはエルゴード定理によって保証されています。しかし、重要な違いがあります：

    ナイーブヒストグラムアプローチは、軌道が状態空間の特定の領域を訪れる長期的な確率のみを提供します。転送演算子はその情報もエンコードしますが、状態間の*遷移確率*を知るという追加の利点があります（[`transfermatrix`](@ref）を参照）。


関連情報: [`InvariantMeasure`](@ref).
