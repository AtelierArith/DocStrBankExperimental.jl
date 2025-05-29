```
add_noise(;
    # キーワード引数
    Cτ_exact::AbstractVector{T},
    τ::AbstractVector{T},
    σ::T,
    ξ::T,
    sum_rule::Function = C0 -> 1 - C0,
    noise_type::Symbol = :TruncatedNormal
) where {T<:AbstractFloat}

add_noise(
    # 引数
    N_samples::Int;
    # キーワード引数
    Cτ_exact::AbstractVector{T},
    τ::AbstractVector{T},
    σ::T,
    ξ::T,
    sum_rule::Function = C0 -> 1 - C0,
    noise_type::Symbol = :TruncatedNormal
) where {T<:AbstractFloat}
```

虚時間相関関数 $C(\tau)$ にノイズを加えます。これは虚時間で指数的に相関しています。

## 引数

  * `N_samples` (オプション): 生成するランダムサンプルの数。この関数に渡すと、異なるサンプルに対応する列を持つ行列が返されます。

## キーワード引数

  * `Cτ_exact::AbstractVector{T}`: $C(\tau)$ の正確な値を含むベクトル。
  * `τ::AbstractVector{T}`: $C(\tau)$ が評価される虚時間 $\tau$ グリッドを指定するベクトル。最後の要素が逆温度に等しいと仮定します。すなわち、`τ[end] = β`。
  * `σ::T`: ノイズの標準偏差; エラーの典型的な振幅を制御します。
  * `ξ::T`: 虚時間におけるノイズに関連する相関長。
  * `sum_rule::Function = C0 -> 1 - C0`: 虚時間における和の法則または境界条件を強制します。デフォルトの動作はフェルミオン相関関数を仮定し、$C(\beta) = 1 - C(0)$ を強制します。
  * `noise_type::Symbol = :TruncatedNormal`: 虚時間における相関が導入される前にノイズがサンプリングされる分布。利用可能なオプションは `noise_type ∈ (:TruncatedNormal, :Gamma, :Normal)` です。

## 追加情報

相関関数 $C(\tau_i)$ に対して、対応するノイズのある相関関数は次のように与えられます。

$$
C_{\rm noisy}(\tau_i) = C(\tau_i) + \frac{\sum_j e^{-|\tau_j-\tau_i|/\xi} R_j}{\sum_j e^{-2|\tau_j-\tau_i|/\xi}},
$$

ここで、和は周期的境界条件を仮定して行われます。`noise_type = :Normal` の場合、サンプリングされたランダム数は $R_j \sim {\rm Normal}(0,\sigma)$ に従います。それ以外の場合、

$$
R_j \sim {\rm sign}(C(\tau_j)) \cdot P(|C(\tau_j)|, \sigma) - C(\tau_j)
$$

ここで、$P(|C(\tau_j)|, \sigma)$ は平均と標準偏差がそれぞれ $|C(\tau_j)|$ と $\sigma$ であるガンマまたは切断正規分布です。

切断正規分布とガンマ分布のサポートは $[0,\infty)$ です。正規分布が使用される場合、$C_{\rm noisy}(\tau_i)$ が $C(\tau_i)$ と異なる符号を持つ可能性があることに注意してくださいが、他の2つの分布ではそれは不可能です。
