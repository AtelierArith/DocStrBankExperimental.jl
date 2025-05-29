```
groupreduce(f, t, by = pkeynames(t); select)
```

Calculate a [`reduce`](@ref) operation `f` over table `t` on groups defined by the values in selection `by`.  The result is put in a table keyed by the unique `by` values.

# Examples

```
t = table([1,1,1,2,2,2], 1:6, names=[:x, :y])
groupreduce(+,        t, :x; select = :y)
groupreduce((sum=+,), t, :x; select = :y)  # change output column name to :sum

t2 = table([1,1,1,2,2,2], [1,1,2,2,3,3], 1:6, names = [:x, :y, :z])
groupreduce(+, t2, (:x, :y), select = :z)

# different reducers for different columns
groupreduce((sumy = :y => +, sumz = :z => +), t2, :x)
```
