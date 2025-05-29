```
dropmissing(t        )
dropmissing(t, select)
```

Drop rows of table `t` which contain missing values (either `Missing` or `DataValue`),  optionally only using the columns in `select`.  Column types will be converted to  non-missing types.  For example:

  * `Vector{Union{Int, Missing}}` -> `Vector{Int}`
  * `DataValueArray{Int}` -> Vector{Int}

# Example

```
t = table([0.1,0.5,missing,0.7], [2,missing,4,5], [missing,6,missing,7], names=[:t,:x,:y])
dropmissing(t)
dropmissing(t, (:t, :x))
```
