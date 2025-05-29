```
finduniq(id)
```

Find the indexes making unique the IDs in a ID vector.

  * `id` : A vector of IDs.

Can be used to remove duplicated rows in a dataset, identified by a single ID variable.

## Examples

```julia
using Jchemo

v = ["a", "d", "c", "b", "a", "d", "a"]  # a vector of IDs

s = finduniq(v)  # indexes of the IDs without duplicates
v[s]  
```
