```
gatherdofnums!(self::F, dest::A, conn::CC) where {F<:AbstractField, A, CC}
```

Gather dofnums from the field.

The order is: for each node  in the connectivity, copy into the buffer all the degrees of freedom for that node,  then the next node  and so on.
