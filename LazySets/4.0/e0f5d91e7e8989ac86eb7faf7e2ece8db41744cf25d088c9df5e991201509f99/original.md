# Extended help

```
isboundedtype(::Type{<:LazySet})
```

### Notes

Note that some sets may still represent an unbounded set even though their type actually does not (example: [`HPolytope`](@ref), because the construction with non-bounding linear constraints is allowed).

### Algorithm

The default implementation returns `false`. All set types that can determine boundedness should override this behavior.
