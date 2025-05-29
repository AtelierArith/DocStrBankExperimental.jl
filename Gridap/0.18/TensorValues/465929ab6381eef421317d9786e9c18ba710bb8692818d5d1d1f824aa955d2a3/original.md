```
num_components(::Type{<:Number})
num_components(a::Number)
```

Total number of components of a `Number` or `MultiValue`, that is 1 for scalars and the product of the size dimensions for a `MultiValue`. This is the same as `length`.
