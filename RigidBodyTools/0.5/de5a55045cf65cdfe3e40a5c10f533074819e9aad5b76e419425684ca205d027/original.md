```
angular_only(v::AbstractPluckerVector)
```

Returns a Plucker vector with only the angular part of the motion or force vector `v` available for subsequent operations. Note that no copy of the original data in `v` is made. Rather, this simply provides a lazy reference to the angular data in `v`.
