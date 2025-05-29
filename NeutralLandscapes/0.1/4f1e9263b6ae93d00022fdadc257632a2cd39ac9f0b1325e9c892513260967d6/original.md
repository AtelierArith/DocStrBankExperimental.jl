```
DiamondSquare <: NeutralLandscapeMaker

DiamondSquare(; H = 0.5) 
DiamondSquare(H)
```

This type generates a neutral landscape using the diamond-squares algorithm, which produces fractals with variable spatial autocorrelation.

https://en.wikipedia.org/wiki/Diamond-square_algorithm

The algorithm is named diamond-square because it is an iterative procedure of "diamond" and "square" steps.

The degree of spatial autocorrelation is controlled by a parameter `H`, which varies from 0.0 (low autocorrelation) to 1.0 (high autocorrelation) –-  note this is non-inclusive and H = 0 and H = 1 will not behave as expected. The result of the diamond-square algorithm is a fractal with dimension D = 2 + H.

A similar algorithm, midpoint-displacement, functions almost identically, except that in DiamondSquare, the square step interpolates edge midpoints from the nearest two corners and the square's center, where as  midpoint-displacement only interpolates from the nearest corners (see `MidpointDisplacement`).
