```
linear_map!(Zout::Zonotope, M::AbstractMatrix, Z::Zonotope)
```

Compute the concrete linear map of a zonotope, storing the result in `Zout`.

### Input

  * `Zout` – zonotope (output)
  * `M`    – matrix
  * `Z`    – zonotope

### Output

The zonotope `Zout`, which is modified in-place.
