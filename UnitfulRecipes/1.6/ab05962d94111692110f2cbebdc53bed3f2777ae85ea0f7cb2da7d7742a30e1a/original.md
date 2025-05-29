```
P_str(s)
```

Creates a string that will be Protected from recipe passes.

Example:

```julia
julia> plot(rand(10)*u"m", xlabel=P"This label is protected")

julia> plot(rand(10)*u"m", xlabel=P"This label is not")
```
