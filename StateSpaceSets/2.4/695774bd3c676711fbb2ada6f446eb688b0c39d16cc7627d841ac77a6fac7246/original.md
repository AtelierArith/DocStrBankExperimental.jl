```
standardize(x::AbstractVector{<:Real}) = (x - mean(x))/std(x)
```
