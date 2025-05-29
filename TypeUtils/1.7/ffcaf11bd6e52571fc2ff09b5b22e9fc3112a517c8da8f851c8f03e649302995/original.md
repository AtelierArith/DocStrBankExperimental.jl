```
return_type(f, argtypes...) -> T
```

yields the type of the result returned by the callable object `f` when called with arguments of types `argtypes...`.

See the warning in the documentation of `Base.promote_op` for the fragility of such inference in some cases. There are no such issues if `f` is an instance of [`TypeStableFunction`](@ref), e.g. built by [`as_return`][@ref), however `argtypes...` are not checked for validity for such objects.
