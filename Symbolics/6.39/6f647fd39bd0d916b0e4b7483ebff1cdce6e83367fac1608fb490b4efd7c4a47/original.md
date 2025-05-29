```
right_inverse(f)
```

Given a single-input single-output function `f`, return its right inverse `g`. This requires that `f` is surjective. If `right_inverse` is defined for a function, `left_inverse` and `inverse` must not be defined and should error. `left_inverse(g)` should also be defined to return `f`.

See also [`inverse`](@ref), [`left_inverse`](@ref), [`@register_inverse`](@ref).
