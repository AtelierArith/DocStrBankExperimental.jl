```
origin(t::Transform{<:Real}) -> Vec3
```

Assuming t is a 3D rigid transform representing a local left-handed coordinate system, this function will return the fourth column, containing the translation part of the transform in 3D.
