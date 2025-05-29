```
drawpath(cp::Path; action=:none, startnewpath=true)
drawpath(cp::Path, action; startnewpath=true)
```

Make the Luxor path stored in `cp` and apply the `action`.

To make paths, follow some path construction functions such as `move()`, `line()`, and `curve()` with the `storepath()` function.

By default, `startnewpath=true`, which starts a new path, discarding any existing path contents.
