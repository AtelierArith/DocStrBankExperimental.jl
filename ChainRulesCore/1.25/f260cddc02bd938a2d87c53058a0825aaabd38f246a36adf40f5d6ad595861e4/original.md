```
NoTangent() <: AbstractZero
```

This tangent indicates that the derivative does not exist. It is the tangent type for primal types that are not differentiable, such as integers or booleans (when they are not being used to represent floating-point values). The only valid way to perturb such values is to not change them at all. As a consequence, `NoTangent` is functionally identical to `ZeroTangent()`, but it provides additional semantic information.

Adding `NoTangent()` to a primal is generally wrong: gradient-based methods cannot be used to optimize over discrete variables. An optimization package making use of this might want to check for such a case.

!!! note
    This does not indicate that the derivative is not implemented, but rather that mathematically it is not defined.


This mostly shows up as the derivative with respect to dimension, index, or size arguments.

```julia
function rrule(fill, x, len::Int)
    y = fill(x, len)
    fill_pullback(ȳ) = (NoTangent(), @thunk(sum(Ȳ)), NoTangent())
    return y, fill_pullback
end
```
