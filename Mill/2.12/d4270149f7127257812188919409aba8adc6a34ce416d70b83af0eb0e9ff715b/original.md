```
NGramIterator(s, n=3, b=256, m=typemax(Int))
```

Construct an [`NGramIterator`](@ref). If `s` is an `AbstractString` it is first converted to integers with `Base.codeunits`.

# Examples

```jldoctest
julia> NGramIterator("deadbeef", 3, 256, 17) |> collect
10-element Vector{Int64}:
  2
 16
  9
  9
  6
 10
 11
 15
  2
  6

julia> NGramIterator(collect(1:9), 3, 10, 1009) |> collect
11-element Vector{Int64}:
 221
 212
 123
 234
 345
 456
 567
 678
 789
 893
 933

julia> Mill.string_start_code()
0x02

julia> Mill.string_end_code()
0x03
```

See also: [`NGramMatrix`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref), [`countngrams`](@ref),     [`countngrams!`](@ref).
