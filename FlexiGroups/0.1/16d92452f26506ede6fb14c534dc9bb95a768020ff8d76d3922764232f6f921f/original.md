```
addmargins(grouping; [combine=flatten])
```

Add margins to a `group` or `groupmap` result for all combinations of group key components.

For example, if a dataset is grouped by `a` and `b` (`keyf=x -> (;x.a, x.b)` in `group`), this adds groups for each `a` value and for each `b` value separately.

`combine` specifies how multiple groups are combined into margins. The default `combine=flatten` concatenates all relevant groups into a single collection.

# Examples

```julia
xs = [(a=1, b=:x), (a=2, b=:x), (a=2, b=:y), (a=3, b=:x), (a=3, b=:x), (a=3, b=:x)]
# basic grouping by unique combinations of a and b
g = group(xs)
map(length, g) == dictionary([(a=1, b=:x) => 1, (a=2, b=:x) => 1, (a=2, b=:y) => 1, (a=3, b=:x) => 3])

# add margins
gm = addmargins(g)
map(length, gm) == dictionary([
    (a=1, b=:x) => 1, (a=2, b=:x) => 1, (a=2, b=:y) => 1, (a=3, b=:x) => 3,  # original grouping result
    (a=1, b=total) => 1, (a=2, b=total) => 2, (a=3, b=total) => 3,  # margins for all values of a
    (a=total, b=:x) => 5, (a=total, b=:y) => 1,  # margins for all values of b
    (a=total, b=total) => 6,  # total
])
```
