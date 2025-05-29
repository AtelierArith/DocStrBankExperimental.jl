```
psi = MPS(physindvec[,regtens=false,oc=1,type=Float64])
```

`psi`をテンソルタイプ`type`のMPSのために構築し、`physindvec`のサイズ(1,`physindvec`[w],1)の空のテンソルを作成します。ここで、wは`physindvec`をインデックス付けし、直交中心`oc`を指定します。`regtens`は、効率のために変換を実行することをデフォルトとする`denstens`タイプへの変換を回避します。
