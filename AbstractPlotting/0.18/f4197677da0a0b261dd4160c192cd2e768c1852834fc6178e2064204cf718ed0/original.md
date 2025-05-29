```
lift(f, o1::Observables.AbstractObservable, rest...)
```

Create a new `Observable` by applying `f` to all observables in `o1` and `rest...`. The initial value is determined by the first function evaluation.
