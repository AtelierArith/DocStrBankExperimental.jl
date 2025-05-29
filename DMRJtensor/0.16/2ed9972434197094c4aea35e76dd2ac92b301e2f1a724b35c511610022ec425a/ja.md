```
D,truncerr = moveL(Lpsi,Rpsi[,cutoff=,m=,minm=,condition=])
```

は、最大ボンド次元 `m`、カットオフ `cutoff`、最小ボンド次元 `minm` を持つ状態で、`psi` の直交中心を左に1スペース移動します。移動中にテンソルの切り捨てをトグルするには `condition` を使用します。SVDから `psi[iL]`、`psi[iR]`、`D` および切り捨て誤差を返します。`Rpsi` を修正します。

参照: [`moveL!`](@ref)
