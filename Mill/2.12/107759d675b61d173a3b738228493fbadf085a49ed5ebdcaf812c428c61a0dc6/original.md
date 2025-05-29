```
countngrams!(o, x, n, b, m=length(o))
```

Count the number of of `n` grams of `x` using base `b` and modulo `m` and store the result to `o`.

# Examples

```jldoctest
julia> o = zeros(Int, 5)
5-element Vector{Int64}:
 0
 0
 0
 0
 0

julia> countngrams!(o, "foo", 3, 256)
5-element Vector{Int64}:
 2
 1
 1
 0
 1
```

See also: [`countngrams`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref),     [`NGramMatrix`](@ref), [`NGramIterator`](@ref).
