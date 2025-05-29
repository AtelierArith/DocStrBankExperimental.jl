```
express(obj, repr::AbstractRepresentation)
express(obj, repr::AbstractRepresentation, use::AbstractUse)
```

Translate a quantum object `obj` to a backend representation `repr`. It is relevant to define `use` for formalism-specific cases, e.g., for `QuantumCliffordRepr`.
