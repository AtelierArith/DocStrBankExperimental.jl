Same as [`@>`](@ref), but threads the last argument.

```
@>> x g(y, z) f == f(g(y, z, x))

@>> x g f(y, z) == f(y, z, g(x))
```

See also: [`@>>`](@ref)
