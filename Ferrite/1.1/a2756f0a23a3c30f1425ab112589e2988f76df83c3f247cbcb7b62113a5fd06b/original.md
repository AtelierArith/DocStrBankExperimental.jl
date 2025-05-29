```
RefTriangle <: AbstractRefShape{2}
```

Reference triangle, reference dimension 2.

```
----------------+--------------------
Vertex numbers: | Vertex coordinates:
    2           |
    | \         | v1: 𝛏 = (1.0, 0.0)
    |   \       | v2: 𝛏 = (0.0, 1.0)
ξ₂^ |     \     | v3: 𝛏 = (0.0, 0.0)
  | 3-------1   |
  +--> ξ₁       |
----------------+--------------------
Edge numbers:   | Edge identifiers:
    +           |
    | \         | e1: (v1, v2)
    2   1       | e2: (v2, v3)
    |     \     | e3: (v3, v1)
    +---3---+   |
----------------+--------------------
Face numbers:   | Face identifiers:
    +           |
    | \         |
    |   \       | f1: (v1, v2, v3)
    |  1  \     |
    +-------+   |
----------------+--------------------
```
