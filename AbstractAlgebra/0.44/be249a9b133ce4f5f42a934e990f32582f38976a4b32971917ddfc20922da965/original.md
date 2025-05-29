```
quo(m::FPModule{T}, subm::FPModule{T}) where T <: RingElement
```

Return the quotient `M` of the module `m` by the module `subm` (which must have been (transitively) constructed as a submodule of `m` or be `m` itself) along with the canonical quotient map from `m` to `M`.
