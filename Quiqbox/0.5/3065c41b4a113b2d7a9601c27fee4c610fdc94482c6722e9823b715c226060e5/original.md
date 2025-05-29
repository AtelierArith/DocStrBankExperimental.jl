```
hasEqual(obj1, obj2, obj3...; 
         ignoreFunction::Bool=false, 
         ignoreContainer::Bool=false,
         decomposeNumberCollection::Bool=false) -> 
Bool
```

Compare if two containers (e.g. `struct`) are equal. An instantiation of  [`hasBoolRelation`](@ref). ≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
begin
    struct S
        a::Int
        b::Float64
    end
    a = S(1, 1.0)
    b = S(1, 1.0)
    c = S(1, 1.0)
    d = S(1, 1.1)

    hasEqual(a, b, c) |> println
    hasEqual(a, b, c, d) |> println
end

# output
true
false
```
