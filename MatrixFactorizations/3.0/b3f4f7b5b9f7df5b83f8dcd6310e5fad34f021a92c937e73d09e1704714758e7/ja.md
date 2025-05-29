```
ReverseCholesky <: Factorization
```

密な対称/エルミート正定値行列 `A` の逆コレスキー分解の行列因子化タイプです。これは、対応する行列因子化関数 [`reversecholesky`](@ref) の戻り値の型です。

三角形の逆コレスキー因子は、因子化 `F::ReverseCholesky` から `F.L` と `F.U` を介して取得でき、ここで `A ≈ F.U * F.U' ≈ F.L' * F.L` です。```
