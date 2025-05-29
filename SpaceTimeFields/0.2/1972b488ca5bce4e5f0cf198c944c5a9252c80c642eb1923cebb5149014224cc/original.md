```
FunctionProfile(f::Function)
```

Create a profile consisting of a specified function `f`. The function must take in a single argument (time) and return a single value.

# Example

```jldoctest
julia> f(t) = 2.0*t

julia> p = SpaceTimeFields.FunctionProfile(f)
Function profile

julia> p(2.0)
4.0
```
