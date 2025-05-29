```
CartesianGrid(lc, hc, n)
```

Create a uniform cartesian grid with lower corner `lc`, upper corner `hc` and and `n` nodes in each direction.

# Examples

```jldoctest; output = true
using LevelSetMethods
a = (0, 0)
b = (1, 1)
n = (10, 4)
grid = CartesianGrid(a, b, n)

# output

CartesianGrid{2, Int64}([0, 0], [1, 1], (10, 4))
```
