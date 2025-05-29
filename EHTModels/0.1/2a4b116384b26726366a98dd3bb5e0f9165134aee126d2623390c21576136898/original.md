```
imanalytic(::Type{<:AbstractModel})
```

Determines whether the model is pointwise analytic in the image domain, i.e. we can evaluate its intensity at an arbritrary point. If `IsAnalytic()` then it will try to call `intensity_point` to calculate the intensity.
