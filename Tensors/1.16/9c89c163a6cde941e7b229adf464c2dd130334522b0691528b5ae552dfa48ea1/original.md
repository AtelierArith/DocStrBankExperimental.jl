```
otimes(::Vec)
```

Compute the open product of a vector with itself. Return a `SymmetricTensor`.

# Examples

```jldoctest
julia> A = rand(Vec{2})
2-element Vec{2, Float64}:
 0.32597672886359486
 0.5490511363155669

julia> otimes(A)
2×2 SymmetricTensor{2, 2, Float64, 3}:
 0.106261  0.178978
 0.178978  0.301457
```
