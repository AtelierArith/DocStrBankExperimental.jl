```
struct BooleanTruth <: Truth
    flag::Bool
end
```

Structure for representing the Boolean truth values ⊤ and ⊥. It wraps a flag which takes value `true` for ⊤ ([`TOP`](@ref)), and `false` for ⊥ ([`BOT`](@ref))

See also [`BooleanAlgebra`](@ref).
