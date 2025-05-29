```
elementwise(f)
```

Alias for `Base.Fix1(broadcast, f)`.

In the case where `f::ComposedFunction`, the result is `Base.Fix1(broadcast, f.outer) ∘ Base.Fix1(broadcast, f.inner)` rather than `Base.Fix1(broadcast, f)`.
