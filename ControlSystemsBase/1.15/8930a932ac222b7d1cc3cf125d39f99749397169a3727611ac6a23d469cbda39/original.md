```
observer_predictor(sys::AbstractStateSpace, K; h::Int = 1, output_state = false)
observer_predictor(sys::AbstractStateSpace, R1, R2[, R12]; output_state = false)
```

If `sys` is continuous, return the observer predictor system

$$
\begin{aligned}
x̂' &= (A - KC)x̂ + (B-KD)u + Ky \\
ŷ  &= Cx + Du
\end{aligned}
$$

with the input equation `[B-KD K] * [u; y]`

If `sys` is discrete, the prediction horizon `h` may be specified, in which case measurements up to and including time `t-h` and inputs up to and including time `t` are used to predict `y(t)`.

If covariance matrices `R1, R2` are given, the kalman gain `K` is calculated using [`kalman`](@ref).

If `output_state` is true, the output is the state estimate `x̂` instead of the output estimate `ŷ`.

See also [`innovation_form`](@ref), [`observer_controller`](@ref) and [`observer_filter`](@ref).
