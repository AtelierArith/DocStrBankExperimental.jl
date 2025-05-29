```
@isinit a.b
```

Check if the lazy field `b` in the object `a` is initialized. Throw a `NonLazyFieldException` if `b` is not a lazy field of `a`. Macro version of [`isinit(a, :b)`](@ref)

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
