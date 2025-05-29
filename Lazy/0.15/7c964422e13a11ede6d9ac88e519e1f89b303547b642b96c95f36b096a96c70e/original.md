The threading macro is like a more flexible version of the [`|>`](@ref) operator.

```
@> x f = f(x)
@> x g f == f(g(x))
@> x a b c d e == e(d(c(b(a(x)))))
```

Unlike [`|>`](@ref), functions can have arguments - the value preceding a function will be treated as its first argument

```
@> x g(y, z) f == f(g(x, y, z))

@> x g f(y, z) == f(g(x), y, z)
```

See also [`@>>`](@ref), [`@as`](@ref).
