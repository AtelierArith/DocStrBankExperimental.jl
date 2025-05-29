```
@forward_interface T [field=_field] [interface=name] [map=_map] [key=value...]
```

Forwards the methods defined for `interface` to objects of type `T`

# Arguments

`name` must be one of (:iteration, :indexing, :array, :vector, :dict, :lockable, :getfields, :setfields), with `name` value `f` corresponding to the interface definition function `$f_interface` (e.g., `array` => `array_interface`).

If `name` is either `getfields` or `setfields`, then the `field` keyword argument is ignored 

Otherwise, `_field` must be one of the following expressions

  * `k::Symbol` or `k::QuoteNode`, or an expression of the form `getfield(_, k)`, in which case methods will be forwarded to `getfield(x, k)`
  * an expression of the form `getproperty(_, k)`, in which case methods will be forwarded to `getproperty(x, k)`
  * an expression of the form `t[args...]`, in which case methods will be forwarded to `x[args...]`
  * or an expression of the form `f(_)` for a single-argument function `f`, in which case methods will be forwarded to `f(x)`

# Additional Arguments

The `key=value` pairs will be forwarded to the corresponding interface definition method. In particular, specifying `omit=func1` or `omit=[func1,func2, ..., funcn]` will omit `func1`, ..., `funcn` from being forwarded by this macro.

See also [`@forward_methods`](@ref)
