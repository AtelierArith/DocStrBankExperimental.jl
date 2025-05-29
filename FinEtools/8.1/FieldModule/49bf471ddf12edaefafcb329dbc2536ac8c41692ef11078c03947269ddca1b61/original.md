```
gathervalues_asvec!(
    self::F,
    dest::AbstractArray{T,1},
    conn::CC,
) where {F<:AbstractField, T, CC}
```

Gather values from the field into a vector.

The order is: for each node  in the connectivity, copy into the buffer all the degrees of freedom,  then the next node and so on.

`dest` = destination buffer: overwritten  inside,  must be preallocated in the correct size

The order of the loops matters, outer loop goes through the connectivity, inner loop goes through the degrees of freedom for each entity.
