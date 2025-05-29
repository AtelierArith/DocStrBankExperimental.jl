```
intensity_point(model::AbstractModel, x, y, args...)
```

Function that computes the pointwise intensity if the model has the trait in the image domain `IsAnalytic()`. Otherwise it will use construct the image in visibility space and invert it.
