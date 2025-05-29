```
jordan_block(expr,square_size::Integer)
```

次のサイズの正方形のジョルダンブロック行列 `J` を計算します：`square_size`。

`J` のエントリは、`J[i,i] = expr` で i = 1,...,n の場合、`J[i,i+1] = 1` で i = 1,...,n-1 の場合、その他のエントリはすべて 0 です。
