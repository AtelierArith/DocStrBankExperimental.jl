```
@define_interface T [interface=name] [kwargs...]
```

Defines the `interface` for objects of type `T`

# Arguments

`name` must be one of (:properties, :equality, :setfields, :getfields), with `name` value `f` corresponding to the interface definition function `$f_interface` (e.g., `array` => `array_interface`).

The `key=value` pairs will be forwarded to the corresponding interface definition method. In particular, specifying `omit=func1` or `omit=[func1,func2, ..., funcn]` will omit `func1`, ..., `funcn` from being forwarded by this macro.

Refer to the documentation of each :name_interface for the specific keyword arguments required, if any. 
