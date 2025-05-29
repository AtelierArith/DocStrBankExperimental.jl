```
interpolate_datafields_2D(Original::CartData, New::CartData; Rotate=0.0, Translate=(0,0,0), Scale=(1.0,1.0,1.0))
```

Interpolates a data field `Original` on a 2D CartData grid `New`. Typically used for horizontal surfaces.

Note: `Original` should have orthogonal coordinates. If it has not, e.g., because it was rotated, you'll have to specify the angle `Rotate` that it was rotated by
