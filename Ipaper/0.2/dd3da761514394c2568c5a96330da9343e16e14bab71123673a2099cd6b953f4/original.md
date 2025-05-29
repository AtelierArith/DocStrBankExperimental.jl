```
match2(x, y)
```

# Examples

```julia
## original version
mds = [1, 4, 3, 5]
md = [1, 5, 6]

findall(r_in(mds, md))
indexin(md, mds)

## modern version
x = [1, 2, 3, 3, 4]
y = [0, 2, 2, 3, 4, 5, 6]
match2(x, y)
```

# Note: match2 only find the element in `y`
