```
rmove(pt)
```

Begin a new subpath in the current path, add `pt` to the current path's current point, then update the current point.

Other path-building functions are `move()`, `line()`, `curve()`, `arc()`, and `rline()`.

There must be a current point before you call this function.

See also `currentpoint()` and `hascurrentpoint()`.
