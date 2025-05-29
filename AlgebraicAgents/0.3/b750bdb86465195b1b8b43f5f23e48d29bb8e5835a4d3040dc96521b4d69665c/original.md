```
⊕(models::Vararg{AbstractAlgebraicAgent, N}; name)
```

Algebraic sum of algebraic models. Optionally specify resulting model's name.

By default, outputs an instance of `FreeAgent`.

# Examples

```julia
⊕(m1, m2; name="diagram1") ⊕ ⊕(m3, m4; name="diagram2");
```
