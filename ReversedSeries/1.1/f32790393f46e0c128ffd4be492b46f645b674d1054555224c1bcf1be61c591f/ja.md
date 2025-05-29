```julia
negative_slope_currently(a; i, back) -> Any

```

aが現在下向きに傾斜している場合はtrueを返します。言い換えれば、`a[i] < a[i+back]`です。
