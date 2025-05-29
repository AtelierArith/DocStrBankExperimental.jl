```
mapn(f, a1::F{T1}, a2::F{T2}, a3::F{T3}, ...) -> F{T}
```

Apply a function over applicative contexts instead of plain values. Similar to `Base.map`, however sometimes the semantic differs slightly. `TypeClasses.mapn` always follows the semantics of `TypeClasses.flatmap` if defined.

E.g. for `Base.Vector` the `Base.map` function zips the inputs and checks for same length. On the other hand `TypeClasses.mapn` combines all combinations of inputs  instead of the zip (which conforms with the semantics of flattening nested Vectors).
