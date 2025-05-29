```
bsubtract(first::Solid, second::Solid)
```

Return new solid after performing `B`-`A`.

```
+-------+            +-------+
|       |            |       |
|   A   |            |       |
|    +--+----+   =   |    +--+
+----+--+    |       +----+
     |   B   |
     |       |
     +-------+
```

# Examples

```julia
c1 = cube(0.5, 0.5, 0.5, 1.0, 1.0, 1.0)
c2 = cube(0.5, 0.5, 0.5, 2.0, 2.0, 2.0)
r = bsubtract(c1, c2) # subtraction of c2 from c1

v = volume(r) # volume of c1-c2
```
