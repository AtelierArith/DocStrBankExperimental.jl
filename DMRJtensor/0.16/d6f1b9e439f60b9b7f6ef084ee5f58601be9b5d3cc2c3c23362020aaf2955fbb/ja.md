```
psi = MPS(physindvec,Ns[,regtens=false,oc=1])
```

`psi`をテンソル型`T`のMPSのために構築します。これは、サイズ(1,`physindvec`[w],1)の空のテンソルを作成し、wが1:`Ns`をインデックスする（`physindvec`で繰り返す）ことで行われます。直交性中心は`oc`です。`regtens`は、効率のために変換を行うことがデフォルトの`denstens`型への変換を回避します。
