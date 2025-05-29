```
ConfigEnumerator{N,S,C} <: AbstractSetNumber
```

Set algebra for enumerating configurations, where `N` is the length of configurations, `C` is the size of storage in unit of `UInt64`, `S` is the bit width to store a single element in a configuration, i.e. `log2(# of flavors)`, for bitstrings, it is `1``.

## Fields

  * `data` is a vector of [`StaticElementVector`](@ref) as the solution set.

## Examples

```jldoctest; setup=:(using GenericTensorNetworks)
julia> a = ConfigEnumerator([StaticBitVector([1,1,1,0,0]), StaticBitVector([1,0,0,0,1])])
{11100, 10001}

julia> b = ConfigEnumerator([StaticBitVector([0,0,0,0,0]), StaticBitVector([1,0,1,0,1])])
{00000, 10101}

julia> a + b
{11100, 10001, 00000, 10101}

julia> one(a)
{00000}

julia> zero(a)
{}
```
