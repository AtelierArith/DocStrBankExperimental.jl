```
isinside(p::Point,pointlist::AbstractArray{<:Point,1})
```

Determine whether `p` is inside `pointlist`.

This function was copied from Luxor.jl. It is an implementation of an algorithm due to Hormann and Agathos (2001)
