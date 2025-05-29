```
billiard_mushroom(sl = 1.0, sw = 0.2, cr = 1.0, sloc = 0.0; door = true)
```

Create a mushroom billiard with stem length `sl`, stem width `sw` and cap radius `cr`. The center of the cap (which is Semicircle) is always at `[0, sl]`. The center of the stem is located at `sloc`.

Optionally, the bottom-most `Wall` is a `Door` (see [`escapetime`](@ref)).
