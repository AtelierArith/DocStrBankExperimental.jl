```
JackknifeVector(f::Function, jks::JackknifeVector...)

Construct a JackknifeVector observable by applying `f` to `jks`.
For example, `JackknifeVector(mean, jk1, jk2, jk3)` returns a JackknifeVector observable of the means of `jk1`, `jk2`, and `jk3`.
```
