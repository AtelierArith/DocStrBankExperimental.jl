```julia
fixed_stepsize_warmup_stages(
;
    M,
    middle_steps,
    doubling_stages
)

```

固定ステップサイズのためのウォームアップステージのシーケンスで、共分散のみを調整します：最初は `middle_steps` ステップで、その後、`doubling_stages` 回、ステップ数を2倍にして繰り返します。

[`default_warmup_stages`](@ref) と非常に似ていますが、ステップサイズ調整のみのウォームアップステージは省略されています。
