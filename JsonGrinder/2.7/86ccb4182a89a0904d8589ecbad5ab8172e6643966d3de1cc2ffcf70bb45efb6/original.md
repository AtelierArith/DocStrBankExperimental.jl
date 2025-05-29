```
remove_nulls(js)
```

Return a new document in which all `null` values (represented as `nothing` in julia) are removed.

# Examples

```jldoctest
julia> remove_nulls(Dict("a" => 1, "b" => nothing))
Dict{String, Union{Nothing, Int64}} with 1 entry:
  "a" => 1

julia> [nothing, Dict("a" => 1), nothing, Dict("a" => nothing)] |> remove_nulls
2-element Vector{Dict{String}}:
 Dict("a" => 1)
 Dict{String, Nothing}()
```
