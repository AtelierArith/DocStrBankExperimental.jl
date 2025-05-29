```
observer_predictor(sys::AbstractStateSpace, K; h::Int = 1, output_state = false)
observer_predictor(sys::AbstractStateSpace, R1, R2[, R12]; output_state = false)
```

もし `sys` が連続の場合、オブザーバ予測システムを返します

$$
\begin{aligned}
x̂' &= (A - KC)x̂ + (B-KD)u + Ky \\
ŷ  &= Cx + Du
\end{aligned}
$$

入力方程式は `[B-KD K] * [u; y]` です。

もし `sys` が離散の場合、予測ホライズン `h` を指定することができ、その場合、時刻 `t-h` までの測定値と時刻 `t` までの入力を使用して `y(t)` を予測します。

共分散行列 `R1, R2` が与えられた場合、カルマンゲイン `K` は [`kalman`](@ref) を使用して計算されます。

`output_state` が真の場合、出力は出力推定値 `ŷ` ではなく状態推定値 `x̂` になります。

さらに [`innovation_form`](@ref)、[`observer_controller`](@ref) および [`observer_filter`](@ref) も参照してください。
