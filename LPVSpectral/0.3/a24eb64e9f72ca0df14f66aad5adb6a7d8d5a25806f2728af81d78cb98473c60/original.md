```
mapwindows(f, W::AbstractWindows)
```

Apply a Function `f` over all windows represented by `W::Windows2`. `f` must take `(y,t)->ŷ` where `y` and `ŷ` have the same length.
