```
check_errs(
    f,
    ȳ::∇ArrayOrScalar,
    x::T,
    v::T,
    ε_abs::∇Scalar=1e-10,
    ε_rel::∇Scalar=1e-7
)::Bool where T
```

Check that the difference between finite differencing directional derivative estimation and RMAD directional derivative computation for function `f` at `x` in direction `v`, for both allocating and in-place modes, has absolute and relative errors of `ε_abs` and `ε_rel` respectively, when scaled by reverse-mode sensitivity `ȳ`.
