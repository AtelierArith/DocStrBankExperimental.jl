```
@uninit! f.b
```

Uninitialize the field `b` in the object `f` Throw a `NonLazyFieldException` if `b` is not a lazy field of `a`. Macro version of [`uninit`](@ref)

```jldoctest
julia> @lazy struct Foo
           @lazy b::Int
       end

julia> f = Foo(uninit)
Foo(uninit)

julia> @isinit f.b
false

julia> @init! f.b = 5
5

julia> @isinit f.b
true
```
