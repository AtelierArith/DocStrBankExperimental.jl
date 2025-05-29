```
function namedtuple(d::Dict)
function namedtuple(;kwargs...)
```

`namedtuple` returns the named tuple formed using keyword arguments or a dictionary passed as parameter.

# Example

```@example
julia> nt = namedtuple(x=1,y=2)
(x = 1, y = 2)
```
