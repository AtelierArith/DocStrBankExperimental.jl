```
autodiff(::ForwardMode, f, Activity, args::Annotation...)
```

Auto-differentiate function `f` at arguments `args` using forward mode.

`args` may be numbers, arrays, structs of numbers, structs of arrays and so on. Enzyme will only differentiate in respect to arguments that are wrapped in a [`Duplicated`](@ref) or similar argument. Unlike reverse mode in [`autodiff`](@ref), [`Active`](@ref) arguments are not allowed here, since all derivative results of immutable objects will be returned and should instead use [`Duplicated`](@ref) or variants like [`DuplicatedNoNeed`](@ref).

`Activity` is the Activity of the return value, it may be:

  * `Const` if the return is not to be differentiated with respect to
  * `Duplicated`, if the return is being differentiated with respect to
  * `BatchDuplicated`, like `Duplicated`, but computing multiple derivatives at once. All batch sizes must be the same for all arguments.

Example returning both original return and derivative:

```jldoctest
f(x) = x*x
res, ∂f_∂x = autodiff(ForwardWithPrimal, f, Duplicated, Duplicated(3.14, 1.0))

# output

(6.28, 9.8596)
```

Example returning just the derivative:

```jldoctest
f(x) = x*x
∂f_∂x = autodiff(Forward, f, Duplicated, Duplicated(3.14, 1.0))

# output

(6.28,)
```
