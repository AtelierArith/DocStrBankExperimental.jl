```
recursively_setproperty!(object, nested_name::Expr, value)
```

Set a nested property of an `object` to `value`, as in the following example:

```julia-repl
julia> mutable struct Foo
           X
           Y
       end

julia> mutable struct Bar
           x
           y
       end

julia> object = Foo(Bar(1, 2), 3)
Foo(Bar(1, 2), 3)

julia> recursively_setproperty!(object, :(X.y), 42)
42

julia> object
Foo(Bar(1, 42), 3)
```
