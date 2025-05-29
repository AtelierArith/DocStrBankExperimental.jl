Reset the elements stored in `s` in batch:

```julia
setElements!(s::SimplexCellList, points, lines, triangles)::Nothing
```

Where `points`, `lines` and `triangles` are collections of collections of objects convertible to  `Point`, `Line`, and `Triangle` respectively.

For example, each collection in `points` is a group of points that can be mapped over independently from, or together with, other groups.

Added elements will have a group index and element index based on the order of the inputs. The first group in each type has group index 1, and the first element in each group has element index 1.
