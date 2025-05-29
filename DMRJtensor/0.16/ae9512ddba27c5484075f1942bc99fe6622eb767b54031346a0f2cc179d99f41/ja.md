```
psi = MPS(physindsize,Ns[,regtens=false,oc=1,type=Float64])
```

`psi`をFloat64のテンソル型のMPSのために構築します。これは、1:`Ns`のwインデックス用にサイズ(1,`physindsize`,1)の空のテンソルを作成し（`physindvec`で繰り返し）、直交性中心`oc`を持ちます。`regtens`は、効率のために変換を実行することがデフォルトの`denstens`型への変換を回避します。
