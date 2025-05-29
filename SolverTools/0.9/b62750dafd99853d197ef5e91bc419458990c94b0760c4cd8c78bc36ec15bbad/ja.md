```
TrustRegion{T, V} <: AbstractTrustRegion{T, V}
```

基本的なトラスト領域タイプで、以下のフィールドを含みます：

  * `initial_radius::T`: 初期半径；
  * `radius::T`: 現在の半径；
  * `max_radius::T`: 半径の上限（デフォルトは `1 / sqrt(eps(T))`）；
  * `acceptance_threshold::T`: 比率がこの閾値（0と1の間）を下回る場合に半径を減少させる（デフォルトは `1e-4`）；
  * `increase_threshold::T`: 比率がこの閾値（0と1の間）を超える場合に半径を増加させる（デフォルトは `0.95`）；
  * `decrease_factor::T`: 0と1の間で減少させる因子（デフォルトは `1 / 3`）；
  * `increase_factor::T`: 1より大きい増加因子（デフォルトは `3 / 2`）；
  * `ratio::T`: 現在の比率 `ared / pred`；
  * `gt::V`: 目的関数の勾配を格納するための事前に割り当てられたメモリベクトル；
  * `good_grad::Bool`: `gt` が試行点での目的関数の勾配である場合は `true`。

以下のコンストラクタが利用可能です：

```
TrustRegion(gt,::V initial_radius::T; kwargs...)
```

`gt` が不明な場合、次のコンストラクタを使用することができます：

```
TrustRegion(::Type{V}, n::Int, Δ₀::T; kwargs...)
TrustRegion(n::Int, Δ₀::T; kwargs...)
```

これにより、サイズ `n` と型 `V` または `Vector{T}` のベクトルが割り当てられます。
