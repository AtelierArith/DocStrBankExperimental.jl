bintersect(first::Solid, second::Solid)

Return new solid after computing intersection of `A` and `B`.

```
+-------+
|       |
|   A   |
|    +--+----+   =   +--+
+----+--+    |       +--+
     |   B   |
     |       |
     +-------+
```

# Examples

```julia
c1 = cube(0.5, 0.5, 0.5, 1.0, 1.0, 1.0)
c2 = cube(0.5, 0.5, 0.5, 2.0, 2.0, 2.0)
r = bintersect(c1, c2) # intersection of c1 and c2

v = volume(r)
```
