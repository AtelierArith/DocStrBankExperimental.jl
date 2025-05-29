```
reset!(think::Think)
```

Reset the computation result of the `think` object.

!!! warning
    Please be aware that `reset!` does not guarantee that a `Think` object will behave exactly as if it has never been evaluated. Some functions that the `Think` object wraps may modify their arguments or depend on external state (i.e., they are not pure functions), which could lead to different results upon re-evaluation.

