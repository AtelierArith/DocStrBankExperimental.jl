```
acwpt(x, wt[, L=maxtransformlevels(x)])
```

配列 `x` の ac ウェーブレットパケット変換を実行します。ウェーブレットタイプ `wt` が変換タイプを決定します。

# 例

```julia
acwpt(x, wavelet(WT.db4))
```

**関連情報:** `iacwpt`
