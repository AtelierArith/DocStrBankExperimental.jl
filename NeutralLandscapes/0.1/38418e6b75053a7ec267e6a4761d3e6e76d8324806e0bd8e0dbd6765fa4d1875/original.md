```
MidpointDisplacement <: NeutralLandscapeMaker

MidpointDisplacement(; H = 0.5)
```

Creates a midpoint-displacement algorithm object `MidpointDisplacement`.  The degree of spatial autocorrelation is controlled by a parameter `H`, which varies from 0.0 (low autocorrelation) to 1.0 (high autocorrelation) –-  note this is non-inclusive and H = 0 and H = 1 will not behave as expected.

A similar algorithm, diamond-square, functions almost identically, except that in diamond-square, the square step interpolates edge midpoints from the nearest two corners and the square's center, where as  `MidpointDisplacement` only interpolates from the nearest corners (see `DiamondSquare`).
