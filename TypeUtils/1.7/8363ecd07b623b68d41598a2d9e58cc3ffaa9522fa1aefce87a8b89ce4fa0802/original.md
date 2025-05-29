```
as_return(T, f) -> g
TypeStableFunction{T}(f) -> g
TypeStableFunction(f, argtypes...) -> g
```

yield a callable object `g` that wraps callable `f` for guaranteed returned type `T`. Alternatively, the type(s) `argtypes...` of the function argument(s) can be specified to infer the returned type `T`. Then the following holds:

```
g(args...; kwds...) === as(T, f(args...; kwds...))
```

for any arguments `args...` and keywords `kwds...`. Note that due to limitation of the `Base.promote_op` method, it is currently not possible to infer `T` based on the types of the keywords.

Methods [`return_type(g)`](@ref) and `parent(g)` may be used to retrieve `T` and `f` respectively.

If `T` is specified, a similar object is given by:

```
g = as(T)∘f
```
