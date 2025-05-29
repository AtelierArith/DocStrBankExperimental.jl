```
SumProductTree{ET} <: AbstractSetNumber
```

Configuration enumerator encoded in a tree, it is the most natural representation given by a sum-product network and is often more memory efficient than putting the configurations in a vector. One can use [`generate_samples`](@ref) to sample configurations from this tree structure efficiently.

## Fields

  * `tag` is one of `ZERO`, `ONE`, `LEAF`, `SUM`, `PROD`.
  * `data` is the element stored in a `LEAF` node.
  * `left` and `right` are two operands of a `SUM` or `PROD` node.

## Examples

```jldoctest; setup=:(using GenericTensorNetworks)
julia> s = SumProductTree(bv"00111")
00111


julia> q = SumProductTree(bv"10000")
10000


julia> x = s + q
+ (count = 2.0)
├─ 00111
└─ 10000


julia> y = x * x
* (count = 4.0)
├─ + (count = 2.0)
│  ├─ 00111
│  └─ 10000
└─ + (count = 2.0)
   ├─ 00111
   └─ 10000


julia> collect(y)
4-element Vector{StaticBitVector{5, 1}}:
 00111
 10111
 10111
 10000

julia> zero(s)
∅



julia> one(s)
00000


```
