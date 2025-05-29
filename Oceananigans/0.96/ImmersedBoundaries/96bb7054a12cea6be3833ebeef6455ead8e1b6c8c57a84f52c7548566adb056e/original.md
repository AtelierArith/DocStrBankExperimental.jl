```
GridFittedBottom(bottom_height, [immersed_condition=CenterImmersedCondition()])
```

Return a bottom immersed boundary.

# Keyword Arguments

  * `bottom_height`: an array or function that gives the height of the                  bottom in absolute $z$ coordinates.
  * `immersed_condition`: Determine whether the part of the domain that is                       immersed are all the cell centers that lie below                       `bottom_height` (`CenterImmersedCondition()`; default)                       or all the cell faces that lie below `bottom_height`                       (`InterfaceImmersedCondition()`). The only purpose of                       `immersed_condition` to allow `GridFittedBottom` and                       `PartialCellBottom` to have the same behavior when the                       minimum fractional cell height for partial cells is set                       to 0.
