```
psi = MPS(type,physindsize,Ns[,regtens=false,oc=1])
```

`psi`を、`physindsize`のサイズの空のテンソルを(1,`physindsize`,1)の形で作成することによって、Float64のテンソルタイプのMPSを構築します。これは、1:`Ns`の範囲でwをインデックス付けし（`physindvec`で繰り返し）、直交性中心`oc`を持ちます。`regtens`は、効率のために変換を行うことがデフォルトの`denstens`タイプへの変換を回避します。
