```
get_icut(c::Cut)
```

Return icut, the control parameter of the cut. 1 for a polar cut, 2 for a conical cut. `TicraUtilities` currently accommodates only `icut == 1`, wherein each cut is for a constant ϕ value.
