```
RefQuadrilateral <: AbstractRefShape{2}
```

Reference quadrilateral, reference dimension 2.

```
----------------+---------------------
Vertex numbers: | Vertex coordinates:
    4-------3   |
    |       |   | v1: 𝛏 = (-1.0, -1.0)
    |       |   | v2: 𝛏 = ( 1.0, -1.0)
ξ₂^ |       |   | v3: 𝛏 = ( 1.0,  1.0)
  | 1-------2   | v4: 𝛏 = (-1.0,  1.0)
  +--> ξ₁       |
----------------+---------------------
Edge numbers:   | Edge identifiers:
    +---3---+   | e1: (v1, v2)
    |       |   | e2: (v2, v3)
    4       2   | e3: (v3, v4)
    |       |   | e4: (v4, v1)
    +---1---+   |
----------------+---------------------
Face numbers:   | Face identifiers:
    +-------+   |
    |       |   |
    |   1   |   | f1: (v1, v2, v3, v4)
    |       |   |
    +-------+   |
----------------+---------------------
```
