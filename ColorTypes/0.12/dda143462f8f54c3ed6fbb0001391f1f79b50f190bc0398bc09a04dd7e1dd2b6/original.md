```
mapreducec(f, op, v0, c)
mapreducec(f, op, c; [init])
```

Reduce across color channels of `c` with the binary operator `op`, first applying `f` to each channel. `v0` or `init` is the neutral element used to initiate the reduction. For grayscale,

```
mapreducec(f, op, v0, c::Gray) = op(v0, f(comp1(c)))
```

whereas for RGB

```
mapreducec(f, op, v0, c::RGB) = op(f(comp3(c)), op(f(comp2(c)), op(v0, f(comp1(c)))))
```

If `c` has an alpha channel, it is always the last one to be folded into the reduction.

!!! compat "ColorTypes 0.12"
    The keyword argument `init` and its omission using the default value require ColorTypes v0.12 or later.

