```
addin!(asm,global,block,ibr,ibc,factor=1.)
```

大きな `out` スパース行列にスパース `block` を追加します。ブロック行と列はそれぞれ `ibr` と `ibc` です。メモリを `global` に割り当て、アセンブラ `asm` を構築するには [`prepare`](@ref) を使用してください。
