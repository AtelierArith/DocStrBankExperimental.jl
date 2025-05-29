```
Alphabet(letters::AbstractVector[, inversions])
```

An alphabet consists of the symbols of a common type `T`.

An `Alphabet` defines a bijection between consecutive integers and its letters, i.e. it can be queried for the index of a letter, or the letter corresponding to a given index.

# Example

```jldoctest
julia> al = Alphabet([:a, :b, :c])
Alphabet of Symbol
  1. a
  2. b
  3. c

julia> al[2]
:b

julia> al[:c]
3

julia> Alphabet([:a, :A, :b], [2, 1, 0])
Alphabet of Symbol
  1. a    (inverse of: A)
  2. A    (inverse of: a)
  3. b
```
