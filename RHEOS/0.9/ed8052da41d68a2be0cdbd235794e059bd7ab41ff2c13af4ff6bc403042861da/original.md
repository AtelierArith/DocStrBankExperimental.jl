```
function dict(nt::NamedTuple)
function dict(;kwargs...)
```

`dict` returns the dictionary formed using keyword arguments or a named tuple passed as parameter.

# Example

```@example
julia> d = dict(x=1,y=2)
Dict{Symbol, Int64} with 2 entries:
  :y => 2
  :x => 1
```
