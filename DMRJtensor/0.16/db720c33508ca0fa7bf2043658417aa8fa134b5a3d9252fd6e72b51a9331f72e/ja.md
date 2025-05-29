```
psi = MPS(A[,regtens=false,oc=psi.oc,type=...])
```

`psi`を、直交中心`oc`を持つテンソル`A`（`network`）を用いてMPSのために構築します。`regtens`は、効率のために変換を行うことがデフォルトの`denstens`型への変換を避けます；`type`は`psi`内のテンソルの入力型にデフォルトします。
