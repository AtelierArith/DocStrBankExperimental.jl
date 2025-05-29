```
abstract type AbstractHtml <: AbstractRenderType end
```

The abstract type for most plain text rendering. Printing is defined using the `AbstractHtml`, so new tables (with different defaults) can be created by subtyping `AbstractHtml` with minimal effort.
