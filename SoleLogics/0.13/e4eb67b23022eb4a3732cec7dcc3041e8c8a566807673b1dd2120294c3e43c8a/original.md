```
struct ExplicitAlphabet{V} <: AbstractAlphabet{V}
    atoms::Vector{Atom{V}}
end
```

An alphabet wrapping atoms in a (finite) `Vector`.

See also [`AbstractAlphabet`](@ref), [`atoms`](@ref).
