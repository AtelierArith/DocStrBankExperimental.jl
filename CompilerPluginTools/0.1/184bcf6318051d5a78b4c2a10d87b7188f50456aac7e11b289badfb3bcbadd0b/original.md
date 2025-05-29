```
JuliaLikeInterpreter <: AbstractInterpreter
```

Abstract type for julia-like interpreter. The subtype of it usually modifies the native julia interpreter a little bit by overloading certain abstract interpretation interface, but forward most of the interfaces to the native interpreter.
