```
replaceproperty!(x, f::Symbol, expected, desired, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

Perform a compare-and-swap operation on `x.f` from `expected` to `desired`, per egal. The syntax `@atomic_replace! x.f expected => desired` can be used instead of the function call form.

See also [`replacefield!`](@ref Core.replacefield!) and [`setproperty!`](@ref Base.setproperty!).
