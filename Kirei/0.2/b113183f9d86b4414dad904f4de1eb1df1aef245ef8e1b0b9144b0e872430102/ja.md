```
@forward Foo.bar f, g(io::IO), h{T}(::Int, arg2) where T
```

`Foo`のメソッド`f`、`g`、`h`を`Foo.bar`にフォワードします。これは`MacroTools.@forward`に似ていますが、指定された型の前に引数をサポートしています。

例えば、上記は次のように等価です。

```julia
f(x::Foo, args...; kwargs...) = f(x.bar, args...; kwargs...)
g(io::IO, x::Foo, args...; kwargs...) = g(io, x.bar, args...; kwargs...)
h{T}(arg1::Int, arg2, x::Foo, args...; kwargs...) where T = h{T}(arg1, arg2, x.bar, args...; kwargs...)
```
