```julia
positive_slope_currently(a; i, back) -> Any

```

現在、aが上昇している場合はtrueを返します。言い換えれば、`a[i] > a[i+back]`です。
