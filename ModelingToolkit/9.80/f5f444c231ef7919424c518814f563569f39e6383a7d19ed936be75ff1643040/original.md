```
ShiftIndex
```

The `ShiftIndex` operator allows you to index a signal and obtain a shifted discrete-time signal. If the signal is continuous-time, the signal is sampled before shifting.

# Examples

```
julia> t = ModelingToolkit.t_nounits;

julia> @variables x(t);

julia> k = ShiftIndex(t, 0.1);

julia> x(k)      # no shift
x(t)

julia> x(k+1)    # shift
Shift(1)(x(t))
```
