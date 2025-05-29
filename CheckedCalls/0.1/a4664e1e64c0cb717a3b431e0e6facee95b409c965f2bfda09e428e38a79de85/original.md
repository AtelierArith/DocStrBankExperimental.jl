```
struct ReturnValueContainsNaN <: Exception
```

Exception to be thrown if the return value `r` of a function `f` is or contains a `NaN` value when called with arguments `args`.

Constructors:

```julia
ReturnValueContainsNaN(r, f, args)
ReturnValueContainsNaN(r, f, args, cause)
```

`cause` is `missing` by default, but should may be set to anything that indicates the cause of the `NaN` value, including another `ReturnValueContainsNaN` instance that was encountered while computing `f(args...)`.
