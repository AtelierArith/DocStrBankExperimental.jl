```
insert!(vin::AbstractVertex, factory::Function, outselect::Function=identity)
```

Replace `vin` as input to all outputs of `vin` with vertex produced by `factory`.

The function `factory` takes `vin` as input.

Example:

```text
Before:

    vin
   / | \
  /  |  \
 v₁ ... vₙ

After:

    vin
     |
   vnew₁
     ⋮
   vnewₖ
   / | \
  /  |  \
 v₁ ... vₙ
```

Note that the connection `vin` -> `vnew₁` as well as all connections `vnewₚ -> vnewₚ₊₁` is done by `factory` in the above example.

The function `outselect` can be used to select a subset of outputs to replace (default all).
