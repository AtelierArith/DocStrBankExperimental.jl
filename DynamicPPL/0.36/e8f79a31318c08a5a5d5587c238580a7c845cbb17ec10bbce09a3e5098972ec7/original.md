```
unfix(context::AbstractContext, syms...)
```

Return `context` but with `syms` no longer fixed.

Note that this recursively traverses contexts, unfixing all along the way.

See also: [`fix`](@ref)
