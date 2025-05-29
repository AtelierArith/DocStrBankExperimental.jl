```
displace_analytical(b::FockBasis, alpha::Number)
displace_analytical(::Type{T}, b::FockBasis, alpha::Number)
```

「解析的」な変位演算子を取得します。その行列要素は、正確な無限次元変位演算子のものと一致します（数値的な不正確さを除いて）。これは、有限次元（切り捨てられた）生成演算子 `a'` と消滅演算子 `a` を使用して行列指数 `exp(alpha * a' - conj(alpha) * a)` を計算する `displace(..., alpha)` の結果とは異なります。
