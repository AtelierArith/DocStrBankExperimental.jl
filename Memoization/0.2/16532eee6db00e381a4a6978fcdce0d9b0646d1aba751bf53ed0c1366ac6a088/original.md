```
@memoize f(x) = ...                # memoize a function definition
@memoize Dict f(x) = ...           # with custom cache type
@memoize LRU(maxsize=4) f(x) = ... # with another custom cache type
@memoize (x::Foo)(y) = ...         # memoize a callable (w.r.t. both x and y)
f(x) = @memoize g(y) = ...         # memoize a closure (w.r.t y, and x if its used)
@memoize h(2)                      # memoize a call to any Julia function
```

When applied to a function definition, memoize a function, closure, or callable, with respect to all of its arguments and keyword arguments. When applied to a function call, memoize just that function call (works with any Julia function).

Memoized closures or callables are memoized on a per-instance basis, so closures are free to use the closed over variables and callables are free to use the fields of the callable object.

By default, an IdDict is used as a cache. Any dict-like object can be used by passing a type or an expression to construct the object as the first argment to the macro before the function definition. For example, if you want to memoize based on the contents of vectors, you could use a `Dict`.
