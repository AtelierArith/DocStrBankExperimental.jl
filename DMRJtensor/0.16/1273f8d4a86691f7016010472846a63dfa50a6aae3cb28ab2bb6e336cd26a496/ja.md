```
D,truncerr = moveL(Lpsi,Rpsi[,cutoff=,m=,minm=,condition=])
```

は、最大結合次元 `m`、カットオフ `cutoff`、最小結合次元 `minm` を持つ状態で、`psi` の直交中心を左に1スペース移動します。移動中にテンソルの切り捨てを `condition` で切り替え、SVDから `psi[iL]`、`psi[iR]`、`D` および切り捨て誤差を返します。`Lpsi` と `Rpsi` は変更されません。

関連情報: [`moveL!`](@ref)
