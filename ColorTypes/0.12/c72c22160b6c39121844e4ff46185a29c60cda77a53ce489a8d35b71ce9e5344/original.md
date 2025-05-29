```
reducec(op, v0, c)
reducec(op, c; [init])
```

Reduce across color channels of `c` with the binary operator `op`. `v0` or `init` is the neutral element used to initiate the reduction. For grayscale,

```
reducec(op, v0, c::Gray) = op(v0, comp1(c))
```

whereas for RGB

```
reducec(op, v0, c::RGB) = op(comp3(c), op(comp2(c), op(v0, comp1(c))))
```

If `c` has an alpha channel, it is always the last one to be folded into the reduction.

!!! compat "ColorTypes 0.12"
    The keyword argument `init` and its omission using the default value require ColorTypes v0.12 or later.

