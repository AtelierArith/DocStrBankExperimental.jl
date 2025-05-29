```
quaternion(θ::Real,v::SVector{3}) -> SVector{4}
```

Form the quaternion $q = w + x\hat{i} + y\hat{j} + z\hat{k}$ from the given rotation angle `θ` and rotation axis `v`. Note that `v` need not be a unit vector.
