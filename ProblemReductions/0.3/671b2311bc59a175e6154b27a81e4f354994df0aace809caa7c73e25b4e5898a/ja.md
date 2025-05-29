```
StaticElementVector{N,S,C}
StaticElementVector(nflavor::Int, x::AbstractVector)
```

`N` はベクトルの長さ、`C` は `UInt64` の単位でのストレージのサイズ、`S` は `log2(# of flavors)` として定義されるストライドです。フレーバーの数が 2 の場合、それは `StaticBitVector` です。

## フィールド

  * `data` は静的要素の構成を格納するための `UInt64` のタプルです。

## 例

```jldoctest; setup=:(using ProblemReductions)
julia> ev = StaticElementVector(3, [1,2,0,1,2])
12012

julia> ev[2]
0x0000000000000002

julia> collect(Int, ev)
5-element Vector{Int64}:
 1
 2
 0
 1
 2
```
