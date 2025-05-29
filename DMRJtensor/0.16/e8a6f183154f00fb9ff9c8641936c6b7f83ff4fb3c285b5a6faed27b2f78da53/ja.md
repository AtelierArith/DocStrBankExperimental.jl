```
psi = MPS(A[,regtens=false,oc=psi.oc,type=...])
```

`psi`をMPSのために構築します。テンソル`A`（MPS形式）と直交中心`oc`を使用します。`regtens`は`denstens`型への変換を回避します（効率のためにデフォルトで変換を行います）；`type`は`psi`内のテンソルの入力型にデフォルトします。
