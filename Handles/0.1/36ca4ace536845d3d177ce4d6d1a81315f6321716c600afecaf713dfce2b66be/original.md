```
@HandleType(n)
```

Create a new type named n to be used as a handle to your resource.

Example: julia> @HandleType(Foo) Foo

julia> foo(x::Integer) = x*x foo (generic function with 1 method)

julia> foo(Foo(2)) 4

julia> foo(x::Foo) = x-x foo (generic function with 2 methods)

julia> foo(Foo(2)) 0
