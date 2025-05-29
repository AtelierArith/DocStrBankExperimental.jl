```
MutableSmallDict{N,K,V} <: AbstractSmallDict{N,K,V}

MutableSmallDict{N,K,V}()
MutableSmallDict{N,K,V}(itr; unique = itr isa AbstractDict)
MutableSmallDict{N,K,V}(key1 => val1, key2 => val2, ...; unique = false)
```

An dictionary with key type `K` and value type `V` that can store up to `N` entries. The dictionary is mutable and implements Julia's dictionary interface.

If the key and value types are omitted, they will be inferred from the pairs or, if possible, from the iterator. If `unique` is set to `true`, then the elements of `itr` are assumed to have distinct keys.

See also [`AbstractSmallDict`](@ref), [`SmallDict`](@ref).

# Examples

```jldoctest
julia> d = MutableSmallDict{8}('a' => 0, 'b' => 1, 'c' => 4)
MutableSmallDict{8, Char, Int64} with 3 entries:
  'a' => 0
  'b' => 1
  'c' => 4


julia> delete!(d, 'b')
MutableSmallDict{8, Char, Int64} with 2 entries:
  'a' => 0
  'c' => 4
```
