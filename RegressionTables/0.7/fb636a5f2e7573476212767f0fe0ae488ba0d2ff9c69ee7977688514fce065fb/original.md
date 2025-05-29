```
abstract type AbstractLatex <: AbstractRenderType end
```

The abstract type for most plain text rendering. Printing is defined using the `AbstractLatex`, so new tables (with different defaults) can be created by subtyping `AbstractLatex` with minimal effort.
