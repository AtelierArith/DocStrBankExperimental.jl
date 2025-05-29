```
SOS2
```

SOS1 (Special Ordered Sets type 2) object than can be used to constrain a vector `x` to a set where at most 2 variables can take a non-zero value, all others being at 0. In addition, if two are non-zero these must be consecutive in their ordering. The `weights` induce an ordering of the variables; as such, they should be unique values. The *k*th element in the set corresponds to the *k*th weight in `weights`. See [here](http://lpsolve.sourceforge.net/5.5/SOS.htm) for a description of SOS constraints and their potential uses. This is a shortcut for the `MathOptInterface.SOS2` set.
