```
autodiff(::ReverseMode, f, Activity, args::Annotation...)
```

Auto-differentiate function `f` at arguments `args` using reverse mode.

Limitations:

  * `f` may only return a `Real` (of a built-in/primitive type) or `nothing`, not an array, struct, `BigFloat`, etc. To handle vector-valued return types, use a mutating `f!` that returns `nothing` and stores it's return value in one of the arguments, which must be wrapped in a [`Duplicated`](@ref).

`args` may be numbers, arrays, structs of numbers, structs of arrays and so on. Enzyme will only differentiate in respect to arguments that are wrapped in an [`Active`](@ref) (for arguments whose derivative result must be returned rather than mutated in place, such as primitive types and structs thereof) or [`Duplicated`](@ref) (for mutable arguments like arrays, `Ref`s and structs thereof).

`Activity` is the Activity of the return value, it may be `Const` or `Active`.

Example:

```jldoctest
a = 4.2
b = [2.2, 3.3]; ∂f_∂b = zero(b)
c = 55; d = 9

f(a, b, c, d) = a * √(b[1]^2 + b[2]^2) + c^2 * d^2
∂f_∂a, _, _, ∂f_∂d = autodiff(Reverse, f, Active, Active(a), Duplicated(b, ∂f_∂b), Const(c), Active(d))[1]

# output

(3.966106403010388, nothing, nothing, 54450.0)
```

here, `autodiff` returns a tuple $(\partial f/\partial a, \partial f/\partial d)$, while $\partial f/\partial b$ will be *added to* `∂f_∂b` (but not returned). `c` will be treated as `Const(c)`.

One can also request the original returned value of the computation.

Example:

```jldoctest
Enzyme.autodiff(ReverseWithPrimal, x->x*x, Active(3.0))

# output

((6.0,), 9.0)
```

!!! note
    Enzyme gradients with respect to integer values are zero. [`Active`](@ref) will automatically convert plain integers to floating point values, but cannot do so for integer values in tuples and structs.

