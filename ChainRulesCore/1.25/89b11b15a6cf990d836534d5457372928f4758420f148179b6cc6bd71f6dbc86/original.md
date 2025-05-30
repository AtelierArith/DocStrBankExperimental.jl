```
is_inplaceable_destination(x) -> Bool
```

Returns true if `x` is suitable for for storing inplace accumulation of gradients. For arrays this means `x .= y` will mutate `x`, if `y` is an appropriate tangent.

Here "appropriate" means that `y` cannot be complex unless `x` is too, and that for structured matrices like `x isa Diagonal`, `y` shares this structure.

!!! note "history"
    Wrapper array types should overload this function if they can be written into. Before ChainRulesCore 1.16, it would guess `true` for most wrappers based on `parent`, but this is not safe, e.g. it will lead to an error with ReadOnlyArrays.jl.


There must always be a correct non-mutating path, so in uncertain cases, this function returns `false`.
