```
psi = MPS(A[,regtens=false,oc=psi.oc,type=...])
```

`psi`をテンソル`A`（テンソルの配列またはMPS）を用いてMPSのために構築します。`oc`は直交中心を示します。`regtens`は効率のために変換を行うことをデフォルトとする`denstens`型への変換を回避します；`type`は`psi`内のテンソルの入力型をデフォルトとします。
