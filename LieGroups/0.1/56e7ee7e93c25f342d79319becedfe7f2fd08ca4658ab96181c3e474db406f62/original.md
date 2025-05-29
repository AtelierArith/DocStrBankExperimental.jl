```
 switch(A::GroupAction{T})
```

Return the group operation action representing the similar [`GroupAction`](@ref) of [`AbstractGroupActionType`](@ref) `T` but acting from the other side. It switches left to right and vice versa. This is done by returning the group action with the “switched” type of `T`.
