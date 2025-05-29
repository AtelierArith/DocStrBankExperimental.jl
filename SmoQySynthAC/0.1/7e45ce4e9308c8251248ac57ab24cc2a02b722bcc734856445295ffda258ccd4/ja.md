```
add_noise!(
    # 引数
    Cτ_noisy::AbstractVector{T};
    # キーワード引数
    Cτ_exact::AbstractVector{T},
    τ::AbstractVector{T},
    σ::T,
    ξ::T,
    sum_rule::Function = C0 -> 1 - C0,
    noise_type::Symbol = :TruncatedNormal
) where {T<:AbstractFloat}

add_noise!(
    # 引数
    Cτ_noisy::AbstractMatrix{T};
    # キーワード引数
    Cτ_exact::AbstractVector{T},
    τ::AbstractVector{T},
    σ::T,
    ξ::T,
    sum_rule::Function = C0 -> 1 - C0,
    noise_type::Symbol = :TruncatedNormal
) where {T<:AbstractFloat}
```

虚時間相関関数 $C(\tau)$ にノイズを加えます。これは虚時間で指数的に相関しています。詳細については [`add_noise`](@ref) を参照してください。

## 引数

  * `Cτ_noisy`: ノイズのある $C(\tau)$ データが書き込まれる配列。行列でありベクトルでない場合、列はサンプルに対応し、行は虚時間スライス $\tau$ に対応します。

## キーワード引数

  * `Cτ_exact::AbstractVector{T}`: $C(\tau)$ の正確な値を含むベクトル。
  * `τ::AbstractVector{T}`: $C(\tau)$ が評価される虚時間 $\tau$ グリッドを指定するベクトル。最後の要素が逆温度に等しいと仮定します。すなわち、`τ[end] = β`。
  * `σ::T`: ノイズの標準偏差; エラーの典型的な振幅を制御します。
  * `ξ::T`: 虚時間におけるノイズに関連する相関長。
  * `sum_rule::Function = C0 -> 1 - C0`: 虚時間における和則または境界条件を強制します。デフォルトの動作はフェルミオン相関関数を仮定し、$C(\beta) = 1 - C(0)$ を強制します。
  * `noise_type::Symbol = :TruncatedNormal`: 虚時間に相関が導入される前にノイズがサンプリングされる分布。利用可能なオプションは `noise_type ∈ (:TruncatedNormal, :Gamma, :Normal)` です。
