```
TrivialCursor{N,P} <: TreeCursor{N,P}
```

A [`TreeCursor`](@ref) which matches the functionality of the underlying node.  Tree nodes wrapped by this cursor themselves have most of the functionality required of a `TreeCursor`, this type exists entirely for the sake of maintaining a fully consistent interface with other `TreeCursor` objects.
