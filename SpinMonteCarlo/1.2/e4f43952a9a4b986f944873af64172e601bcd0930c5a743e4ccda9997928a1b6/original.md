```
Jackknife(f::Function, jks::Jackknife...)

Construct a Jackknife observable by applying `f` to `jks`.
For example, `Jackknife(mean, jk1, jk2, jk3)` returns a Jackknife observable of the means of `jk1`, `jk2`, and `jk3`.
```
