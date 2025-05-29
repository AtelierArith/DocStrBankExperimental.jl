```
PeriodicGraph(key::AbstractString)
PeriodicGraph{N}(key::AbstractString)
```

`key`から`PeriodicGraph{N}`を構築します。`key`は、形式が`"N src1 dst1 ofs1_1 ofs1_2 ... ofs1_N src2 dst2 ofs2_1 ofs2_2 ... ofs2_N  ...  srcm dstm ofsm_1 ofsm_2 ... ofsm_N"`の空白で区切られた値の文字列であり、ここで`N`はグラフの繰り返し次元の数、`m`はエッジの数であり、すべての`i`が`1`と`m`の間で、`i`-thエッジは次のように説明されます。

  * `srci`、ソース頂点の頂点識別子、
  * `dsti`、宛先頂点の頂点識別子、および
  * `(ofsi_1, ofsi_2, ..., ofsi_N)`エッジのオフセット。

このグラフのコンパクトな表現は、単にグラフを`print`するか、`string`を使用することで得られます。

!!! note
    `key`が`g`が`PeriodicGraph{N}`であるときに`string(g)`から取得された場合、より高速な実装のために`parse(PeriodicGraph, key)`または`parse(PeriodicGraph{N}, key)`を使用してください。


## 例

```jldoctest
julia> PeriodicGraph("2  1 2 0 0  2 1 1 0  1 1 0 -1")
PeriodicGraph2D(2, PeriodicEdge2D[(1, 1, (0,1)), (1, 2, (-1,0)), (1, 2, (0,0))])

julia> PeriodicGraph3D("3  1 1 0 0 1  1 1 0 1 0  1 1 1 0 0")
PeriodicGraph3D(1, PeriodicEdge3D[(1, 1, (0,0,1)), (1, 1, (0,1,0)), (1, 1, (1,0,0))])

julia> string(ans)
"3 1 1 0 0 1 1 1 0 1 0 1 1 1 0 0"

julia> string(parse(PeriodicGraph3D, ans)) == ans
true
```
