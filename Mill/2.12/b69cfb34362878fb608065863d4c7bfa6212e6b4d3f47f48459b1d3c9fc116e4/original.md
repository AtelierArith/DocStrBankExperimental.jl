```
countngrams(o, x, n, b, m)
```

Count the number of of `n` grams of `x` using base `b` and modulo `m` into a vector of length `m` in case `x` is a single sequence or into a matrix with `m` rows if `x` is an iterable of sequences.

# Examples

```jldoctest
julia> countngrams("foo", 3, 256, 5)
5-element Vector{Int64}:
 2
 1
 1
 0
 1

julia> countngrams(["foo", "bar"], 3, 256, 5)
5×2 Matrix{Int64}:
 2  1
 1  0
 1  2
 0  0
 1  2
```

See also: [`countngrams!`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref),     [`NGramMatrix`](@ref), [`NGramIterator`](@ref).
