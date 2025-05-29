```
Projection(fp::AbstractFlowpipe, vars::NTuple{D,Int}) where {D}
```

フローパイプの遅延射影を返します。

### 入力

### 出力

### 注意事項

射影は遅延であり、フローパイプ内の各集合 `X` を、与えられた変数 `vars` に関連付けられた射影行列 `M` を用いて `MX` にマッピングすることから成ります。
