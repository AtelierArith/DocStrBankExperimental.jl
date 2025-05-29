```
shannon_entropy( probabilities :: AbstractVector ) :: Float64
```

確率分布の古典的エントロピー：

$$
S = -\sum_{i=1}^n p_i \log_2(p_i)
$$

入力 `probabilities` が [`is_probability_distribution`](@ref) を満たさない場合、`DomainError` がスローされます。
