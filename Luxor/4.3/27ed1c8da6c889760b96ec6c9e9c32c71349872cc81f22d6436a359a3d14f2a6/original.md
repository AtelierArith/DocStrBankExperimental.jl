```
hascurrentpoint()
```

Return true if there is a current point. This is the most recent point in the current path, as defined by one of the path building functions such as `move()`, `line()`, `curve()`, `arc()`, `rline()`, and `rmove()`.

To obtain the current point, use `currentpoint()`.

There's no current point after `strokepath()` and `strokepath()` calls.
