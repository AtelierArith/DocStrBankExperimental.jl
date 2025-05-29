```
psi = MPS(T,physindvec,Ns[,regtens=false,oc=1])
```

テンソル型 `T` の MPS のために `psi` を構築します。これは、サイズ (1,`physindvec`[w],1) の空のテンソルを w が 1:`Ns` をインデックスする形で作成します（`physindvec` で繰り返し）。直交性中心は `oc` です。`regtens` は効率のために変換を行うことをデフォルトとする `denstens` 型への変換を回避します。
