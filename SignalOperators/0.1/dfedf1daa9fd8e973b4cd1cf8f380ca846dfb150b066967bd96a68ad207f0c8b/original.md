```
fadeto(x,y,[len=10ms],[fn=x->sinpi(0.5x)])
```

Append x to y, with a smooth transition lasting `len` seconds fading from `x` to `y` (so the total length is `duration(x) + duration(y) - len`).

This fade is accomplished with a [`rampoff`](@ref) of `x` and a [`rampon`](@ref) for `y`. `fn` should be non-decreasing with a range of [0,1] over the domain [0,1]. It should map over the entire range: that is  `fn(0) == 0` and `fn(1) == 1`.

Both `len` and `fn` are optional arguments: either one or both can be specified, though `len` must occur before `fn` if present.
