```
moments(R::TSFrame)
```

Calculates the `(statistical) moments` of `asset returns`. Output is a `NamedArray`.

# Example

```julia
julia> pmoments = moments(returns)
4×4 Named Matrix{Float64}
Tickers ╲ Moments │      Mean        Std   Skewness   Kurtosis
──────────────────┼───────────────────────────────────────────
TSLA              │ 0.0431772   0.149608    1.36882    2.19682
NFLX              │  0.010848  0.0637211   0.604374  -0.808401
MSFT              │ 0.0366371  0.0603753   0.681468   0.790701
```

# Output:

  * `NamedArray`; rows: `tickers`, columns: `moments`

# Notes:

  * `Kurtosis`: `excess kurtosis`
