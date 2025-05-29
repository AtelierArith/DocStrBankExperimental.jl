```
updateconn!(self::ET, newids::Vector{IT}) where {ET<:AbstractFESet, IT}
```

Update the connectivity after the IDs of nodes changed.

`newids`= new node IDs. Note that indexes in the conn array "point" *into* the  `newids` array. After the connectivity was updated this will no longer be true!
