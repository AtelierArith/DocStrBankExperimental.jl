```
GeneralObservableLogger(observable::Function, T, n_steps)
```

A logger which holds a record of regularly sampled observations of a system.

`observable` should return an object of type `T` and support the method `observable(s::System, neighbors; n_threads::Integer)::T`.
