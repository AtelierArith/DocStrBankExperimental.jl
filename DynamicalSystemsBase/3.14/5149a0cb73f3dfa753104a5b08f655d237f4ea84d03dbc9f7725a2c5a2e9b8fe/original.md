```
PlaneCrossing(plane, dir) → pc
```

Create a struct that can be called as a function `pc(u)` that returns the signed distance of state `u` from the hyperplane `plane` (positive means in front of the hyperplane). See [`PoincareMap`](@ref) for what `plane` can be (tuple or vector).
