A representation of a Julia type that does not need the type to be defined in the Julia session, and can be stored as a string. This is done by storing the type name and the module it belongs to as Symbols.

!!! warning
    While `QualifiedType` is currently quite capable, it is not currently able to express the full gamut of Julia types. In future this will be improved, but it will likely always be restricted to a certain subset.


# Subtyping

While the subtype operator cannot work on QualifiedTypes (`<:` is a built-in), when the Julia types are defined the subset operator `⊆` can be used instead. This works by simply `convert`ing the QualifiedTypes to the corresponding Type and then applying the subtype operator.

```julia-repl
julia> QualifiedTypes(:Base, :Vector) ⊆ QualifiedTypes(:Core, :Array)
true

julia> Matrix ⊆ QualifiedTypes(:Core, :Array)
true

julia> QualifiedTypes(:Base, :Vector) ⊆ AbstractVector
true

julia> QualifiedTypes(:Base, :Foobar) ⊆ AbstractVector
false
```

# Constructors

```julia
QualifiedType(parentmodule::Symbol, typename::Symbol)
QualifiedType(t::Type)
```

# Parsing

A QualifiedType can be expressed as a string as `"$parentmodule.$typename"`. This can be easily `parse`d as a QualifiedType, e.g. `parse(QualifiedType, "Core.IO")`.
