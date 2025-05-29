```julia
passagecontains(urn1, urn2)

```

True if passage component of `urn1` contains or is equal to passage component of `urn2`.

# Examples

```julia-repl
julia>
passagecontains(CtsUrn("urn:cts:greekLit:tlg0012.tlg001:1.1")
CtsUrn("urn:cts:greekLit:tlg0012.tlg001:1")
)
```
