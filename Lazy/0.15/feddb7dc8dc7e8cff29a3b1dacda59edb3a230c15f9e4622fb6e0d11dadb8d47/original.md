Enables efficient recursive functions, e.g.

```
@rec reduce(f::Function, v, xs::List) =
  isempty(xs) ? v : reduce(f, f(v, first(xs)), tail(xs))
```

Without `@rec` this function would overflow the stack for lists of 80,000 or more elements.

Caveats:

  * No support for trampolining, i.e. only calls to the   given function are optimised away.
  * Ignores multiple dispatch – it is assumed that the function's   name always refers to the given definition.
  * Don't rebind the function's name in a let (see above).
  * Don't use this with varargs functions.

Use the more flexible, but slower, [`@bounce`](@ref) to avoid these issues.
