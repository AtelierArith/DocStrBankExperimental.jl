```
throttle(dt, input, f=(acc,x)->x, init=value(input), reinit=x->x;
            typ=typeof(init), name=auto_name!(string("throttle ",dt,"s"), input), leading=false)
```

Throttle a signal to update at most once every dt seconds. By default, the throttled signal holds the last update of the `input` signal during each `dt` second time window.

This behavior can be changed by the `f`, `init` and `reinit` arguments. The `init` and `f` functions are similar to `init` and `f` in `foldp`. `reinit` is called when a new throttle time window opens to reinitialize the initial value for accumulation, it gets one argument, the previous accumulated value.

For example     `y = throttle(0.2, x, push!, Int[], _->Int[])` will create vectors of updates to the integer signal `x` which occur within 0.2 second time windows.

If `leading` is `true`, the first update from `input` will be sent immediately by the throttle signal. If it is false, the first update will happen `dt` seconds after `input`'s first update

New in v0.4.1: `throttle`'s behaviour from previous versions is now available with the `debounce` signal type.
