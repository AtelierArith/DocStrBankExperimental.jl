```
StaticElementVector{N,S,C}
StaticElementVector(nflavor::Int, x::AbstractVector)
```

`N` is the length of vector, `C` is the size of storage in unit of `UInt64`, `S` is the stride defined as the `log2(# of flavors)`. When the number of flavors is 2, it is a `StaticBitVector`.

## Fields

  * `data` is a tuple of `UInt64` for storing the configuration of static elements.

## Examples

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
