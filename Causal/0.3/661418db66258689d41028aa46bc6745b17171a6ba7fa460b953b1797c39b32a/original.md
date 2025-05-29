```julia
applycallbacks(obj)

```

Calls the callbacks of `obj` if the callbacks are not nothing.

# Example

```julia
julia> mutable struct MyType{CB}
       x::Int
       callbacks::CB
       end

julia> obj = MyType(5, Callback(condition=obj -> obj.x > 0, action=obj -> println("x is positive")));

julia> applycallbacks(obj)
x is positive

julia> obj.x = -1
-1

julia> applycallbacks(obj)
```
