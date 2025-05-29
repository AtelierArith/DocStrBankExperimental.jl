```
melt_list(list; deepcopy=false, kw...)
```

# Arguments

  * `list`: list of DataFrames

# Examples

```julia
d = data.table(; x=1, y=2)
l = [d, d, d, d]

r1 = melt_list(l, id=1:4) # id all is 4
r2 = melt_list(l, id=1:4, deepcopy=true)

melt_list(l; a = 1, b = 2)
```
