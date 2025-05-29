```
ShiftIndex
```

The `ShiftIndex` operator allows you to index a signal and obtain a shifted discrete-time signal. If the signal is continuous-time, the signal is sampled before shifting.

# Examples

```
julia> @variables t x(t);

julia> k = ShiftIndex(t, 0.1);

julia> x(k)      # no shift
x(t)

julia> x(k+1)    # shift
Shift(t, 1)(x(t))
```
