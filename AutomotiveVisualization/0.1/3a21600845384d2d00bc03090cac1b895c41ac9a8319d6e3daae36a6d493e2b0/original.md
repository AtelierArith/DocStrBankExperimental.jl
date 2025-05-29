```
TargetFollowCamera <: Camera
```

Camera which follows the vehicle with ID `target_id`. By default, the target vehicle is tracked in x and y direction. Tracking in either direction can be disabled by setting the  `x` or `y` keys to a desired value.

# Constructor

`TargetFollowCamera(target_id; x=NaN, y=NaN, kwargs...)`
