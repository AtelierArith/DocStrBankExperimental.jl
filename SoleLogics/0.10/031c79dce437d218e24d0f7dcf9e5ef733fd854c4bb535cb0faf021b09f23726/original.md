```
struct NamedConnective{Symbol} <: Connective end
```

A singleton type for representing connectives defined by a name or a symbol.

# Examples

The AND connective (i.e., the logical conjunction) is defined as the subtype:

```
const CONJUNCTION = NamedConnective{:∧}()
const ∧ = CONJUNCTION
arity(::typeof(∧)) = 2
```

See also [`NEGATION`](@ref), [`CONJUNCTION`](@ref), [`DISJUNCTION`](@ref), [`IMPLICATION`](@ref), [`Connective`](@ref).
