```
D,truncerr = moveR(Lpsi,Rpsi[,cutoff=,m=,minm=,condition=])
```

は、最大ボンド次元 `m`、カットオフ `cutoff`、最小ボンド次元 `minm` を持つ `psi` の直交中心を右に1スペース移動します。移動中にテンソルの切り捨てを `condition` で切り替えます。SVDから `psi[iL]`、`psi[iR]`、`D` および切り捨て誤差を返します。

関連情報: [`moveR!`](@ref)
