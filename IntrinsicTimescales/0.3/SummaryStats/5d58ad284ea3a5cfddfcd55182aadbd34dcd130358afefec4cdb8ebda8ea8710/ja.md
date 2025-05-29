```
bat_integrated_autocorr_weight(
    samples::DensitySampleVector;
    c::Integer = 5, tol::Integer = 50, strict = true
)
```

`samples`の統合自己相関重みを推定します。

[`bat_integrated_autocorr_len`](@ref)を使用します。
