```
typedmap(::Type{T}, c...) 
typedmap(f, ::Type{T}, c...)
```

Transform collection `c` by applying `f` to each element. For multiple collection arguments, apply `f` elementwise, and stop when any of them   is exhausted. The element type of returned collection will be forced to `T`. In addtion, `typedmap(T, c...)` is equivalent to `typedmap(T, T, c...)`.
