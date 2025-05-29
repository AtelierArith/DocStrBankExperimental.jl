```
TRONTrustRegion{T, V} <: AbstractTrustRegion{T, V}
```

TRONによって使用される信頼領域は、以下のフィールドを含みます：

  * `initial_radius::T`: 初期半径;
  * `radius::T`: 現在の半径;
  * `max_radius::T`: 半径の上限（デフォルトは `1 / sqrt(eps(T))`）;
  * `acceptance_threshold::T`: この閾値が0と1の間で比率が下回る場合に半径を減少させる（デフォルトは `1e-4`）;
  * `decrease_threshold::T`: ...0と1の間（デフォルトは `0.25`）;
  * `increase_threshold::T`: この閾値が0と1の間で比率が上回る場合に半径を増加させる（デフォルトは `0.75`）;
  * `large_decrease_factor::T`: 0と1の間の減少因子（デフォルトは `0.25`）;
  * `small_decrease_factor::T`: 0と1の間の減少因子（デフォルトは `0.5`）;
  * `increase_factor::T`: 1より大きい増加因子（デフォルトは `4`）;
  * `ratio::T`: 現在の比率 `ared / pred`;
  * `quad_min::T`: ...;
  * `gt::V`: 目的関数の勾配を格納するための事前に割り当てられたメモリベクター;
  * `good_grad::Bool`: `gt`が試行点での目的関数の勾配である場合は `true`。

以下のコンストラクタが利用可能です：

```
TRONTrustRegion(gt,::V initial_radius::T; kwargs...)
```

`gt`が不明な場合、以下のコンストラクタを使用することができます：

```
TRONTrustRegion(::Type{V}, n::Int, Δ₀::T; kwargs...)
TRONTrustRegion(n::Int, Δ₀::T; kwargs...)
```

これにより、サイズ `n` と型 `V` または `Vector{T}` のベクターが割り当てられます。
