```
moments(R::TSFrame)
```

`資産リターン`の`(統計的)モーメント`を計算します。出力は`NamedArray`です。

# 例

```julia
julia> pmoments = moments(returns)
4×4 Named Matrix{Float64}
Tickers ╲ Moments │      Mean        Std   Skewness   Kurtosis
──────────────────┼───────────────────────────────────────────
TSLA              │ 0.0431772   0.149608    1.36882    2.19682
NFLX              │  0.010848  0.0637211   0.604374  -0.808401
MSFT              │ 0.0366371  0.0603753   0.681468   0.790701
```

# 出力:

  * `NamedArray`; 行: `ティッカー`, 列: `モーメント`

# 注意:

  * `Kurtosis`: `超過尖度`
