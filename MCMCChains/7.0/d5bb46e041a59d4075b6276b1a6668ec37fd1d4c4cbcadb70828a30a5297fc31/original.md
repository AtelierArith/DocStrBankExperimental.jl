```
namesingroup(chains::Chains, sym::Union{AbstractString,Symbol}; index_type::Symbol=:bracket)
```

Return the parameters with the same name `sym`, but have a different index. Bracket indexing format in the form of `:sym[index]` is assumed by default. Use `index_type=:dot` for parameters with dot  indexing, i.e. `:sym.index`.

If the chain contains a parameter of name `:sym` it will be returned as well.

# Example

```jldoctest
julia> chn = Chains(rand(100, 2, 2), ["A[1]", "A[2]"]);

julia> namesingroup(chn, :A)
2-element Vector{Symbol}:
 Symbol("A[1]")
 Symbol("A[2]")

julia> # Also works for specific elements.
       namesingroup(chn, Symbol("A[1]"))
1-element Vector{Symbol}:
 Symbol("A[1]")

```

```jldoctest
julia> chn = Chains(rand(100, 3, 2), ["A.1", "A.2", "B"]);

julia> namesingroup(chn, :A; index_type=:dot)
2-element Vector{Symbol}:
 Symbol("A.1")
 Symbol("A.2")
```
