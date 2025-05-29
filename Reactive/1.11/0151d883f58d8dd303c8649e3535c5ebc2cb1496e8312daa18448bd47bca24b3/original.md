```
debounce(dt, input, f=(acc,x)->x, init=value(input), reinit=x->x;
            typ=typeof(init), name=auto_name!(string("debounce ",dt,"s"), input))
```

Creates a signal that will delay updating until `dt` seconds have passed since the last time `input` has updated. By default, the debounce signal holds the last update of the `input` signal since the debounce signal last updated.

This behavior can be changed by the `f`, `init` and `reinit` arguments. The `init` and `f` functions are similar to `init` and `f` in `foldp`. `reinit` is called after the debounce sends an update, to reinitialize the initial value for accumulation, it gets one argument, the previous accumulated value.

For example     `y = debounce(0.2, x, push!, Int[], _->Int[])` will accumulate a vector of updates to the integer signal `x` and push it after `x` is inactive (doesn't update) for 0.2 seconds.
