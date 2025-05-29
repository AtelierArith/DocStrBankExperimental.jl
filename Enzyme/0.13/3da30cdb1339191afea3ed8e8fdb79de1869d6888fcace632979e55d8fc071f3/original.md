```
autodiff_thunk(::ReverseModeSplit, ftype, Activity, argtypes::Type{<:Annotation}...)
```

Provide the split forward and reverse pass functions for annotated function type ftype when called with args of type `argtypes` when using reverse mode.

`Activity` is the Activity of the return value, it may be `Const`, `Active`, or `Duplicated` (or its variants `DuplicatedNoNeed`, `BatchDuplicated`, and `BatchDuplicatedNoNeed`).

The forward function will return a tape, the primal (or nothing if not requested), and the shadow (or nothing if not a `Duplicated` variant), and tapes the corresponding type arguements provided.

The reverse function will return the derivative of `Active` arguments, updating the `Duplicated` arguments in place. The same arguments to the forward pass should be provided, followed by the adjoint of the return (if the return is active), and finally the tape from the forward pass.

Example:

```jldoctest

A = [2.2]; ∂A = zero(A)
v = 3.3

function f(A, v)
    res = A[1] * v
    A[1] = 0
    res
end

forward, reverse = autodiff_thunk(ReverseSplitWithPrimal, Const{typeof(f)}, Active, Duplicated{typeof(A)}, Active{typeof(v)})

tape, result, shadow_result  = forward(Const(f), Duplicated(A, ∂A), Active(v))
_, ∂v = reverse(Const(f), Duplicated(A, ∂A), Active(v), 1.0, tape)[1]

result, ∂v, ∂A 

# output

(7.26, 2.2, [3.3])
```
