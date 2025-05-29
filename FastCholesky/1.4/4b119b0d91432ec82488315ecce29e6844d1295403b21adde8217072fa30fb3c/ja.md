```
cholsqrt(input)
```

入力行列 `input` のコレスキー平方根を計算します。この関数は `fastcholesky(input).L` のエイリアスです。注意: これは文献で使用される標準的な行列平方根とは異なり、結果が対称であることを要求します。

```jldoctest
julia> A = [4.0 2.0; 2.0 5.0];

julia> A_sqrt = cholsqrt(A);

julia> isapprox(A_sqrt * A_sqrt', A)
true
```
