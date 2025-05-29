```
EdgeGradient <: NeutralLandscapeMaker

EdgeGradient(; direction=360rand())
EdgeGradient(direction)
```

This type is used to generate an edge gradient landscape, where values change as a bilinear function of the *x* and *y* coordinates. The direction is expressed as a floating point value, which will be in *[0,360]*. The inner constructor takes the mod of the value passed and 360, so that a value that is out of the correct interval will be corrected.
