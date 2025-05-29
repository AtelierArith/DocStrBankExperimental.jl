```
sethue("black")
sethue(0.3, 0.7, 0.9)
setcolor(sethue("red")..., .2)
```

Set the color without changing opacity.

`sethue()` is like `setcolor()`, but we sometimes want to change the current color without changing alpha/opacity. Using `sethue()` rather than `setcolor()` doesn't change the current alpha opacity.

See also [`setcolor`](@ref).
