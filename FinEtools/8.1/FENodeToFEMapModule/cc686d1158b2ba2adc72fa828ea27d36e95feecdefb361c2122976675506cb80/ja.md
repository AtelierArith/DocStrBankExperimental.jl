```
FENodeToFEMap(conn::Vector{NTuple{N, IT}}, nmax::FInt) where {N, IT<:Integer}
```

有限要素ノードからそれらを接続する有限要素へのマップ。

  * `conns` = タプルのベクトルとしての接続性
  * `nmax` = 最大のノード番号

例:

```
m = FENodeToFEMap(fes.conn, count(fens))
```
