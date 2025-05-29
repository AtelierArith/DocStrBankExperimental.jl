```
ViewElements(Inds::Union{AbstractArray, Tuple, Colon, Int}) -> Function
```

Produces a function `X::AbstractArray{<:Number}->view(X, Inds)`` for viewing indices of an array wrapped inside struct for more informative stack traces.
