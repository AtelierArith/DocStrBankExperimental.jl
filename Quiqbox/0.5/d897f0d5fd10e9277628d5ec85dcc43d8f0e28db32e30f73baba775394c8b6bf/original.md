```
hasIdentical(obj1, obj2, obj3...; 
             ignoreFunction::Bool=false, 
             ignoreContainer::Bool=false,
             decomposeNumberCollection::Bool=false) -> 
Bool
```

Compare if two containers (e.g. `struct`) are the Identical. An instantiation of  [`hasBoolRelation`](@ref).

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
begin
    struct S
        a::Int
        b::Vector{Float64}
    end

    a = S(1, [1.0, 1.1])
    b = a
    c = b
    d = S(1, [1.0, 1.1])

    hasIdentical(a, b, c) |> println
    hasIdentical(a, b, c, d) |> println
end

# output
true
false
```
