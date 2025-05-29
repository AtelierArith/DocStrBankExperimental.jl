```
setinverse(f, invf)
```

Return a function that behaves like `f` and uses `invf` as its inverse.

Useful in cases where no inverse is defined for `f` or to set an inverse that is only valid within a given context, e.g. only for a limited argument range that is guaranteed by the use case but not in general.

For example, `asin` is not a valid inverse of `sin` for arbitrary arguments of `sin`, but can be a valid inverse if the use case guarantees that the argument of `sin` will always be within `-π` and `π`:

```jldoctest
julia> foo = setinverse(sin, asin);

julia> x = π/3;

julia> foo(x) == sin(x)
true

julia> inverse(foo)(foo(x)) ≈ x
true

julia> inverse(foo) === setinverse(asin, sin)
true
```
