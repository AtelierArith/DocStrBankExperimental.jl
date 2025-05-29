```
bunion(first::Solid, second::Solid)
```

Return new solid after union of `A` and `B`.

```
+-------+            +-------+
|       |            |       |
|   A   |            |       |
|    +--+----+   =   |       +----+
+----+--+    |       +----+       |
     |   B   |            |       |
     |       |            |       |
     +-------+            +-------+
```

# Examples

```julia
c1 = cube(0.5, 0.5, 0.5, 1.0, 1.0, 1.0)
c2 = cube(0.5, 0.5, 0.5, 2.0, 2.0, 2.0)
r = bunion(c1, c2) # union of solids c1 and c2

v = volume(r) # volume of union c1 c2
```
