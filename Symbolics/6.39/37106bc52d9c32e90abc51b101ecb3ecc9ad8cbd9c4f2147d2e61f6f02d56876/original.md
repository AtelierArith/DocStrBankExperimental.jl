```
left_inverse(f)
```

Given a single-input single-output function `f`, return its left inverse `g`. This requires that `f` is injective. If `left_inverse` is defined for a function, `right_inverse` and `inverse` must not be defined and should error. `right_inverse(g)` should also be defined to return `f`.

See also: [`inverse`](@ref), [`right_inverse`](@ref), [`@register_inverse`](@ref).
