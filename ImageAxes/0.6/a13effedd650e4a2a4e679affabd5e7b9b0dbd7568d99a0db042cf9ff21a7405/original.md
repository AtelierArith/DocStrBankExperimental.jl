```
TimeAxis{Ax}
```

A trait (from SimpleTraits) indicating whether axis `Ax` corresponds to time. This decision is based on the symbol-name given to `Ax`. For example, the following declares that all `Axis{:time}` objects correspond to time:

```
@traitimpl TimeAxis{Axis{:time}}
```

This definition has already been made in ImageAxes, but you can add new names as well.
