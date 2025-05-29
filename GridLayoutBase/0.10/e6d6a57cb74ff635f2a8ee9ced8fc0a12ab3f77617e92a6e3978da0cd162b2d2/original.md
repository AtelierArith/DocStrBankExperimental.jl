```
with_updates_suspended(f::Function, gl::GridLayout; update = true)
```

Disable layout updates for `gl` and call the function `f`. If `update` is true, force a layout update after `f` returns.
