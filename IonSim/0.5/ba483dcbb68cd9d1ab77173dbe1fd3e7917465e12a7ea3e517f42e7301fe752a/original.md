```
zeemanshift(I, sublevel, T::Chamber)
```

Calls `zeemanshift(I::Ion, sublevel, B::Real)` with `B` evaluated for ion `I` in `T`. `I` may be either an Ion or an Int indicating the desired ion's index within `T`.
