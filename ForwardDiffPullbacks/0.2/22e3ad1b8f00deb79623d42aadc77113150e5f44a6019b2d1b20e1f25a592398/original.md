```
fwddiff(f)::Function
```

Use `ForwardDiff` dual numbers to implement `ChainRulesCore` pullbacks For

  * `fwddiff(f)(args...)
  * `fwddiff(f).(args...)

Example:

```
using ForwardDiffPullbacks, StaticArrays

f = (xs...) -> (sum(map(x -> sum(map(x -> x^2, x)), xs)))
xs = (2, (3, 4), SVector(5, 6, 7))
f(xs...) == 139

using ChainRulesCore

y, back = rrule(fwddiff(f), xs...)
y == 139
map(unthunk, back(1)) == (NoTangent(), 4, (6, 8), [10, 12, 14])

using Zygote

Zygote.gradient(fwddiff(f), xs...) == Zygote.gradient(f, xs...)

Xs = map(x -> fill(x, 100), xs)
Zygote.gradient((Xs...) -> sum(fwddiff(f).(Xs...)), Xs...) ==
    Zygote.gradient((Xs...) -> sum(f.(Xs...)), Xs...)
```

The gradient is the same with and without `fwddiff`, but `fwddiff` makes the gradient calculation a lot faster here.
