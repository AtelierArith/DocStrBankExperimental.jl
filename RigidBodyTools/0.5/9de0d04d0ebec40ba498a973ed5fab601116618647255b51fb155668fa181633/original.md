```
DeformationMotion(u::Function,v::Function)
```

Create an instance of directly-specified velocity whose components are specified with functions. These functions `u` and `v` must each be of the form `f(x̃,ỹ,t)`, where `x̃` and `ỹ` are coordinates of a point in the body coordinate system and `t` is time, and they must return the corresponding velocity component in the body coordinate system.
