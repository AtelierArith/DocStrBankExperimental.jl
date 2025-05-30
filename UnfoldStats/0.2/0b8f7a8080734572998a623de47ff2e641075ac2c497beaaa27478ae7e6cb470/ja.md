```
extract_coefs(models::Vector{<:UnfoldModel}, predictor, basisname)
```

Unfoldモデルのベクトルに適用されると、すべてのモデル（通常は被験者）に対して係数（予測子と基準名に一致する）を抽出し、それらを連結します。

返される係数の次元は、チャネル x 時間 x 係数 x 被験者です。
