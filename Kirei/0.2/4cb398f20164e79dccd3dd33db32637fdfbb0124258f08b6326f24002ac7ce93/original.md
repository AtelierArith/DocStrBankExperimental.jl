```
@variadic_ccall [lib] cfunc(arg0::T0, arg1::T1; varargs...)::TR
```

Used in a `@generated` function to call a variadic C function.

Only simple types are supported.

Example:

```julia
@generated printf(fmt, varargs...) = @variadic_ccall printf(s::Cstring; varargs...)::Cint
```
