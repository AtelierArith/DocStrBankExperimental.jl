```
readhrse(hrse::IO; options=HrseReadOptions(); type=nothing)
readhrse(hrse::String; options=HrseReadOptions(); type=nothing)
```

Reads an HRSE file from the given IO object or string and returns the corresponding Julia object. The `options` argument can be used to configure the parser. Lists will be read as vectors, pairs as a Pair, symbols and strings as a String, and  numeric types as the corresponding Julia type defined in the parser options. If `type` is given, the result will be parsed as the given type using its StructTypes.StructType.

# Examples

```jldoctest
julia> using HumanReadableSExpressions

julia> hrse = """
       alpha:
           1 2 3 4
           5 6
           7 8 9
       beta: (0 . 3)
       gamma:
           a: 1
           b: 2
           c: "c"
       """;

julia> readhrse(hrse)
3-element Vector{Pair{String}}:
 "alpha" => [[1, 2, 3, 4], [5, 6], [7, 8, 9]]
  "beta" => (0 => 3)
 "gamma" => Pair{String}["a" => 1, "b" => 2, "c" => "c"]
```

See also [`HrseReadOptions`](@ref).
