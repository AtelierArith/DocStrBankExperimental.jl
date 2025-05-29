```
NamedDimsArray{L, T, N, A}(data)
```

A `NamedDimsArray` is a wrapper array type, that provides a view onto  the orignal array, which can have its dimensions refer to name rather than by position.

For example:

```
xs = NamedDimsArray{(:features, :observations)}(data);

n_obs = size(xs, :observations)
feature_totals = sum(xs; dims=:observations)

first_obs_vector = xs[observations=1]
x = x[observations=15, features=2]  # 2nd feature in 15th observation.
```

`NamedDimsArray`s are normally a (near) zero-cost abstraction. They generally resolve most dimension name related operations at compile time.

The `NamedDimsArray` constructor takes a list of names as `Symbol`s, one per dimension, and an array to wrap. If the array being wrapped is a `NamedDimsArray` already then the new names are combined with the existing names – to replace wildcards (`:_`). This will throw an error if the new names are not compatible with the old names (i.e. if the nonwildcards do not match). To assign new names to a `NamedDimsArray` without regard to compatibility with the old names see `rename`(@ref).
