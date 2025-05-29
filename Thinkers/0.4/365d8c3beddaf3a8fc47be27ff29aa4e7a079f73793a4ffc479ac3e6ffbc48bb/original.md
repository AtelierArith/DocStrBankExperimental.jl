```
reify!(thunk::Thunk)
```

Reify a `Thunk`.

Calculate the value of the expression by recursively evaluating each argument and keyword of the `Thunk`, and then evaluating the `Thunk`'s callable with the evaluated arguments.

If called again, this function will recompute everything from scratch.

!!! warning
    Some functions that the `Think` object wraps may modify their arguments or depend on external state (i.e., they are not pure functions), which could lead to different results upon re-evaluation.

