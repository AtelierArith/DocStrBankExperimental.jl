```
acwt(x, wt[, L=maxtransformlevels(x)])
```

配列 `x` の前方 ac ウェーブレット変換を実行します。このメソッドは 2D ケースでも機能します。ウェーブレットタイプ `wt` は変換タイプを決定します。利用可能なメソッドのリストについては Wavelet.jl を参照してください。

# 例

```julia
acwt(x, wavelet(WT.db4))
```

**関連:** `iacwt`
