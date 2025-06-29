スレッドマクロは、[`|>`](@ref) 演算子のより柔軟なバージョンのようなものです。

```
@> x f = f(x)
@> x g f == f(g(x))
@> x a b c d e == e(d(c(b(a(x)))))
```

[`|>`](@ref) とは異なり、関数は引数を持つことができ - 関数の前にある値はその最初の引数として扱われます。

```
@> x g(y, z) f == f(g(x, y, z))

@> x g f(y, z) == f(g(x), y, z)
```

さらに [`@>>`](@ref)、[`@as`](@ref) も参照してください。
