```
TimeSequence(f, ev, times)
TimeSequence(f, ev_iter)
```

Constructs a TimeSequence by iterating the evolution iterator `ev` and applying the function `f` to each moment.

## Arguments

  * `f`: A function that takes a moment and returns a value. The function is applied to each moment in the evolution.
  * `ev`: An `Evolution` object.
  * `times`: A range of times to evaluate the function at.
  * `ev_iter`: An evoltuion iterator that yields moments. Think of it as `ev(times)`.
