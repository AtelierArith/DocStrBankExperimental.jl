```julia
workcontains(urn1, urn2)

```

True if work component of `urn1` contains or is equal to work component of `urn2`.

# Examples

```julia-repl
julia>
workcontains(CtsUrn("urn:cts:greekLit:tlg0012.tlg001:1.1")
CtsUrn("urn:cts:greekLit:tlg0012.tlg001:1")
)
```
