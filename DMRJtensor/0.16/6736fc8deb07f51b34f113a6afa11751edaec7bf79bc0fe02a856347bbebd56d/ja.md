```
psi = MPS(T,A[,regtens=false,oc=1])
```

は、直交中心 `oc` を持つテンソル `A`（テンソルの配列またはMPS）を使用して、テンソル型 `T` のMPSのための `psi` を構築します。 `regtens` は、効率のために変換を実行することをデフォルトとする `denstens` 型への変換を回避します。
