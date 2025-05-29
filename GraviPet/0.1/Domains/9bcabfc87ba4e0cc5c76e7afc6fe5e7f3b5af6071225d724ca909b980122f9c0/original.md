```
shifted(dom::Domain, shift)::Domain
```

Shift the domain `dom` by moving both domain bounds in the same direction. This does not change the size of the domain.

`shfited(dom, shift)` is equivalent to `expanded(dom, -shift, +shift)`.

See also [`expanded`](@ref).
