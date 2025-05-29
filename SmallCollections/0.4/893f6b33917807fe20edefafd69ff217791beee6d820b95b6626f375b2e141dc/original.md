```
SmallDict{N,K,V} <: AbstractSmallDict{N,K,V}

SmallDict{N,K,V}()
SmallDict{N,K,V}(itr; unique = itr isa AbstractDict)
SmallDict{N,K,V}(key1 => val1, key2 => val2, ...; unique = false)
```

An immutable dictionary with key type `K` and value type `V` that can store up to `N` entries. All entries come from the key-value iterator `itr` provided at construction time or from the explicitly given pairs.

If the key and value types are omitted, they will be inferred from the pairs or, if possible, from the iterator. If `unique` is set to `true`, then the elements of `itr` are assumed to have distinct keys.

See also [`AbstractSmallDict`](@ref), [`MutableSmallDict`](@ref).

# Examples

```jldoctest
julia> SmallDict{8}(Int16(1) => 2, Int32(3) => 4.0)
SmallDict{8, Int32, Float64} with 2 entries:
  1 => 2.0
  3 => 4.0

julia> SmallDict{8,Char,Int}('a'+k => k^2 for k in 0:2; unique = true)
SmallDict{8, Char, Int64} with 3 entries:
  'a' => 0
  'b' => 1
  'c' => 4
```
