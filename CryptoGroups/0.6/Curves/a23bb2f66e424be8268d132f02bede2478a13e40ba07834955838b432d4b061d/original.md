```
concretize_type(::Type{ECPoint{P}}, order::Integer, cofactor::Integer; name=nothing) where P <: AbstractPoint
```

Constructs an `ECPoint` for a concrete point type `P <: AbstractPoint` with specified order and cofactor. The name is used for aliasing group parameters with `@ECPoint{name}` display semantics. 
