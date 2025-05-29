```
RectangularCluster <: NeutralLandscapeMaker

RectangularCluster(; minimum=2, maximum=4)
RectangularCluster(minimum, [maximum=4])
```

Fills the landscape with rectangles containing a random value. The size of each rectangle/patch is between `minimum` and `maximum` (the two can be equal for a fixed size rectangle).
