```
flat_coeffs!(flat::AbstractVector{<:Real}, mxh::MXH)
```

すべての mxh コエフィシエントを長さ 5 + 2L の浮動小数点数の配列として返します。ここで L は sin/cos コエフィシエントの数です。

注意: `flat` 入力ベクトルに対してインプレースで動作し、自動微分には対応していません。
