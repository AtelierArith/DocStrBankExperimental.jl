```
abstract type AbstractAscii <: AbstractRenderType end
```

The abstract type for most plain text rendering. Printing is defined using the `AbstractAscii`, so new tables (with different defaults) can be created by subtyping `AbstractAscii` with minimal effort.
