```
function set_previous_window_func(f)
```

Set the function `f` to be the one that will be called to check whether the user wants the previous window. The signature must be:

```
f(k::Keystroke)::Bool
```

It must return `true` if the previous window is required of `false` otherwise.
