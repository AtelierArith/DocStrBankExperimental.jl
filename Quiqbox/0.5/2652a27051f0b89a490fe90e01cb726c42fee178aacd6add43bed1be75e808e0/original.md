```
markUnique(arr::AbstractArray{T}, args...; 
           compareFunction::Function=hasEqual, kws...) where {T} -> 
Tuple{Vector{Int}, Vector{T}}
```

Return a `Vector{Int}` whose elements are indices to mark the elements inside `arr` such  that same element will be marked with same index, and a `Vector{T}` containing all the  unique elements. The definition of "unique" (or "same") is based on `compareFunction`  which is set to [`hasEqual`](@ref) in default. `args` and `kws` are placeholders for the  positional arguments and keyword arguments for `compareFunction` respectively.

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
markUnique([1, [1, 2],"s", [1, 2]])

# output
([1, 2, 3, 2], Any[1, [1, 2], "s"])
```

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
begin
    struct S
        a::Int
        b::Float64
    end

    a = S(1, 2.0)
    b = S(1, 2.0)
    c = S(1, 2.1)
    d = a

    markUnique([a,b,c,d])
end

# output
([1, 1, 2, 1], S[S(1, 2.0), S(1, 2.1)])
```
