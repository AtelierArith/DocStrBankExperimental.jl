@variables args...

create **FD** variables to use in symbolic expressions. Example:

```julia
julia> @variables x y
y

julia> f = x*y
(x * y)
```
