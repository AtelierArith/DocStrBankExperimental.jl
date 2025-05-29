```
stretch(f::AbstractGP, l::Union{AbstractVecOrMat{<:Real}, Real})
```

This is the primary mechanism by which to introduce length scales to your programme.

If `l isa Real` or `l isa AbstractMatrix{<:Real}`, `stretch(f, l)(x) == f(l * x)` for any input `x`. In the `l isa Real` case, this is equivalent to scaling the length scale by `1 / l`.

`l isa AbstractVector{<:Real}` is equivalent to `stretch(f, Diagonal(l))`.

Equivalent to `f ∘ Stretch(l)`.
