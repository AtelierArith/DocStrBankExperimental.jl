```
information(est::DifferentialInfoEstimator, x) → h::Real
```

提供された [`DifferentialInfoEstimator`](@ref) と入力データ `x` を使用して **微分情報量測定** を推定します。

## 説明

圧倒的多数の微分推定器は [`Shannon`](@ref) エントロピーを推定します。同じ推定器が異なる情報量測定を推定できる場合（例えば、[`Shannon`](@ref) と [`Tsallis`](@ref) の両方を推定できる場合）、情報量測定は推定器自体への引数として提供されます。

すべての微分情報量測定推定器については、ドキュメント内の [微分情報量測定推定器の表](@ref table_diff_ent_est) を参照してください。

現在、離散情報量測定とは異なり、このメソッドは確率密度関数を明示的に最初に計算し、その後この密度を情報量測定の定義に渡すことはありません。しかし、将来的には [`probabilities`](@ref) API に似た `density` API を確立したいと考えています。

## 例

測定の微分バージョンを計算するには、最初の引数として [`DifferentialInfoEstimator`](@ref) に渡し、[`information`](@ref) に渡します。

```julia
x = randn(1000)
h_sh = information(Kraskov(Shannon()), x)
h_vc = information(Vasicek(Shannon()), x)
```

正規分布の基底-e Shannon 微分エントロピーは `0.5*log(2π) + 0.5` nats です。

```julia
est = Kraskov(k = 5, base = ℯ) # nats のための基底 `ℯ`。
h = information(est, randn(2_000_000))
abs(h - 0.5*log(2π) - 0.5) # ≈ 0.0001
```
