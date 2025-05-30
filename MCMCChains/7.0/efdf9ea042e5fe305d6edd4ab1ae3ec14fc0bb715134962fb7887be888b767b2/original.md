```
replacenames(chains::Chains, dict::AbstractDict)
```

Replace parameter names by creating a new `Chains` object that shares the same underlying data.

# Examples

```jldoctest
julia> chn = Chains(rand(100, 2, 2), ["one", "two"]);

julia> chn2 = replacenames(chn, "one" => "A");

julia> names(chn2)
2-element Vector{Symbol}:
 :A
 :two

julia> chn3 = replacenames(chn2, Dict("A" => "one", "two" => "B"));

julia> names(chn3) 
2-element Vector{Symbol}:
 :one
 :B
```
