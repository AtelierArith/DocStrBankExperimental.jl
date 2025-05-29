```
PeriodicGraph(key::AbstractString)
PeriodicGraph{N}(key::AbstractString)
```

Construct a `PeriodicGraph{N}` from a `key`, which is a string of whitespace-separated values of the form `"N src1 dst1 ofs1_1 ofs1_2 ... ofs1_N src2 dst2 ofs2_1 ofs2_2 ... ofs2_N  ...  srcm dstm ofsm_1 ofsm_2 ... ofsm_N"` where `N` is the number of repeating dimensions of the graph, `m` is the number of edges and for all `i` between `1` and `m`, the number of edges, the `i`-th edge is described as

  * `srci`, the vertex identifier of the source vertex,
  * `dsti`, the vertex identifier of the destination vertex and
  * `(ofsi_1, ofsi_2, ..., ofsi_N)` the offset of the edge.

This compact representation of a graph can be obtained simply by `print`ing the graph or with `string`.

!!! note
    Use `parse(PeriodicGraph, key)` or `parse(PeriodicGraph{N}, key)` for a faster implementation if `key` was obtained from `string(g)` with `g` a `PeriodicGraph{N}`.


## Examples

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
