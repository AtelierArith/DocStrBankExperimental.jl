```
function set_next_window_func(f)
```

Set the function `f` to be the one that will be called to check whether the user wants the next window. The signature must be:

```
f(k::Keystroke)::Bool
```

It must return `true` if the next window is required of `false` otherwise.
