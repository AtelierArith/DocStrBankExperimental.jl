```julia
corr_cholesky_factor(n)

```

相関行列のコレスキー因子に変換します。

引数が（正の）整数 `n` の場合、出力のサイズ `n × n` を決定し、`Matrix` が生成されます。

引数が `SMatrix{N,N}` の場合、`SMatrix` が生成されます。
