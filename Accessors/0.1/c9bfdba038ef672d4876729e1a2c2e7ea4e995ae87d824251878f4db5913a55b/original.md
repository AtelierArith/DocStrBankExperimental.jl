```
@accessor func
```

Given a simple getter function, define the corresponding `set` method automatically.

# Example

```julia
julia> @accessor my_func(x) = x.a

julia> my_func((a=1, b=2))
1

julia> set((a=1, b=2), my_func, 100)
(a = 100, b = 2)
```
