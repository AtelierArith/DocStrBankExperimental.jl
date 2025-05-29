```
lines_required!(isrequired::AbstractVector{Bool}, src::CodeInfo, edges::CodeEdges;
                norequire = ())
```

Like `lines_required`, but where `isrequired[idx]` has already been set to `true` for all statements that you know you need to evaluate. All other statements should be marked `false` at entry. On return, the complete set of required statements will be marked `true`.

`norequire` keyword argument specifies statements (represented as iterator of `Int`s) that should *not* be marked as a requirement. For example, use `norequire = LoweredCodeUtils.exclude_named_typedefs(src, edges)` if you're extracting method signatures and not evaluating new definitions.
