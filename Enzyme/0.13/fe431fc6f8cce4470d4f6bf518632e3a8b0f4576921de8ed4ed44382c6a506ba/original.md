```
autodiff_thunk(::ForwardMode, ftype, Activity, argtypes::Type{<:Annotation}...)
```

Provide the thunk forward mode function for annotated function type ftype when called with args of type `argtypes`.

`Activity` is the Activity of the return value, it may be `Const` or `Duplicated` (or its variants `DuplicatedNoNeed`, `BatchDuplicated`, and`BatchDuplicatedNoNeed`).

The forward function will return the shadow (or nothing if not a `Duplicated` variant) and the primal (if requested).

Example returning both the return derivative and original return:

```jldoctest
a = 4.2
b = [2.2, 3.3]; ∂f_∂b = zero(b)
c = 55; d = 9

f(x) = x*x
forward = autodiff_thunk(ForwardWithPrimal, Const{typeof(f)}, Duplicated, Duplicated{Float64})
∂f_∂x, res = forward(Const(f), Duplicated(3.14, 1.0))

# output

(6.28, 9.8596)
```

Example returning just the derivative:

```jldoctest
a = 4.2
b = [2.2, 3.3]; ∂f_∂b = zero(b)
c = 55; d = 9

f(x) = x*x
forward = autodiff_thunk(Forward, Const{typeof(f)}, Duplicated, Duplicated{Float64})
∂f_∂x, = forward(Const(f), Duplicated(3.14, 1.0))

# output

(6.28,)
```
