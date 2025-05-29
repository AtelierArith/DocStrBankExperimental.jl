```
winding(P,z)
```

Compute the winding number of a closed curve or path `P` about the point `z`. Each counterclockwise rotation about `z` contributes +1, and each clockwise rotation about it counts -1. The winding number is zero for points not in the region enclosed by `P`. 

The result is unreliable for points lying on `P`, for which the problem is ill-posed.
