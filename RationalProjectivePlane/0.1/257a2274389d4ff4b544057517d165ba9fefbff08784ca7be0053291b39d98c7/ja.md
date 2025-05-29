```
transform(a::PP, aa::PP, b::PP, bb::PP, c::PP, cc::PP)::Matrix{Rational{Int}}
```

行列 `M` を作成します。`M(a) == aa`、`M(b) == bb`、および `M(c) == cc` という性質を持ちます。
