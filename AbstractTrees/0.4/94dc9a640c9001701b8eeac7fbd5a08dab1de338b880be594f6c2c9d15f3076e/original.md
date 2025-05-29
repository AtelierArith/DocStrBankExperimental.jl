```
ImplicitCursor{N,P,S} <: TreeCursor{N,P}
```

A [`TreeCursor`](@ref) which wraps nodes which cannot efficiently access either their parents or siblings directly. This should be thought of as a "worst case scenario" tree cursor.  In particular, `ImplicitCursor`s store the child iteration state of type `S` and for any of `ImplicitCursor`s method to be type-stable it must be possible to infer the child iteration state type, see [`childstatetype`](@ref).
