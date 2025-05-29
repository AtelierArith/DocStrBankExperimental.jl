```
@init! a.b = v
```

Initialize the lazy field `b` in object `a` to `v`. Throw a `NonLazyFieldException` if `b` is not a lazy field of `a`. Throw an `AlreadyInitializedException` if `b` is already initialized. Macro version of `init!(a, :b, v)`

```jldoctest
julia> @lazy struct Foo
           @lazy b::Int
       end

julia> f = Foo(uninit)
Foo(uninit)

julia> f.b
ERROR: field `b` in struct of type `Foo` is not initialized
[...]

julia> @init! f.b = 3
3

julia> f.b
3

julia> @init! f.b = 2
ERROR: field `b` in struct of type `Foo` already initialized
[...]
```
