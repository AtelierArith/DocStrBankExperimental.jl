```
ngrams!(o, x, n=3, b=256)
```

Store codes of `n` grams of `x` using base `b` to `o`.

# Examples

```jldoctest
julia> o = zeros(Int, 5)
5-element Vector{Int64}:
 0
 0
 0
 0
 0

julia> ngrams!(o, "foo", 3, 256)
5-element Vector{Int64}:
  131686
  157295
 6713199
 7302915
 7275267
```

See also: [`ngrams`](@ref), [`countngrams`](@ref),     [`countngrams!`](@ref), [`NGramMatrix`](@ref), [`NGramIterator`](@ref).
