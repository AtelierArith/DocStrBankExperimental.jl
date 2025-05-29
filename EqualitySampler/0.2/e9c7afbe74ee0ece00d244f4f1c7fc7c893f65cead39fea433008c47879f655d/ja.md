```julia
get_hpm_partition(
    results::EqualitySampler.EnumerateResult
) -> Vector{Int64}

```

最高後方確率モデル/パーティションを計算します。サンプリングを介して結果が得られない場合やモデル空間が非常に大きい場合、これは不安定になる可能性があることに注意してください。
