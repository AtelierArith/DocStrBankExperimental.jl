```
spatialidxs(A::ClimArray) → idxs
```

Return an iterable that can be used to access all spatial points of `A` with the syntax

```julia
idxs = spatialidxs(A)
for i in idxs
    slice_at_give_space_point = A[i...]
end
```

Works for all types of space (`...` is necessary because `i` is a `Tuple`).
