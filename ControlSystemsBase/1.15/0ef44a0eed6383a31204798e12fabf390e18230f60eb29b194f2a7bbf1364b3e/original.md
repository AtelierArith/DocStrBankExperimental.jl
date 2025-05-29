```
observer_filter(sys, K; output_state = false)
```

Return the observer filter 

$$
\begin{aligned}
x̂(k|k) &= (I - KC)Ax̂(k-1|k-1) + (I - KC)Bu(k-1) + Ky(k) \\
\end{aligned}
$$

with the input equation `[(I - KC)B K] * [u(k-1); y(k)]`.

Note the time indices in the equations, the filter assumes that the user passes the *current* $y(k)$, but the *past* $u(k-1)$, that is, this filter is used to estimate the state *before* the current control input has been applied. This causes a state-feedback controller acting on the estimate produced by this observer to have a direct term.

This is similar to [`observer_predictor`](@ref), but in contrast to the predictor, the filter output depends on the current measurement, whereas the predictor output only depend on past measurements.

The observer filter is equivalent to the [`observer_predictor`](@ref) for continuous-time systems.

!!! note
    To use this formulation, the observer gain `K` should have been designed for the pair `(A, CA)` rather than `(A, C)`. To do this, pass `direct = true` when calling [`place`](@ref) or [`kalman`](@ref).


Ref: "Computer-Controlled Systems" Eq 4.32
