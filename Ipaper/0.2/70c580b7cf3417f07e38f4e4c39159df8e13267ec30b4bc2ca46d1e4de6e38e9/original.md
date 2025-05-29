```
agg!(R::AbstractArray{FT,3}, A::AbstractArray{<:Real,3}; 
    fact=2, parallel=true, fun=mean)
agg(A::AbstractArray{<:Real,3}; fact=2, parallel=true, fun=mean)
```

Aggregate a 3D array `A` by a factor of `fact` in time dimension (third dim) using the function `fun`.
