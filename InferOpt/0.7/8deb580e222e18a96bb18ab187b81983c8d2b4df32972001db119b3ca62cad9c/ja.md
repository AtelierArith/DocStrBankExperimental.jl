```julia
objective_value(
    f::InferOpt.LinearMaximizer,
    θ,
    y;
    kwargs...
) -> Any

```

与えられた LinearMaximizer `f` の目的関数の値を計算します。重み `θ` と解 `y` を知っている場合、すなわち θᵀg(y) + h(y) です。
