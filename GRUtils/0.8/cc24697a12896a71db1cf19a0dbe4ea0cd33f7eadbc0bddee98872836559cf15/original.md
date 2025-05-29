```
xticks(minor[, major = 1])
yticks(minor[, major = 1])
zticks(minor[, major = 1])
```

Set the `minor`intervals of the ticks for the X, Y or Z axis, and (optionally) the number of minor ticks between `major` ticks.

Use the keyword argument `xticks=(minor, major)`, etc. in plotting functions, to set the tick intervals during the creation of plots (both the minor and major values are required in this case).

# Examples

```julia
# Minor ticks every 0.2 units in the X axis
xticks(0.2)
# Major ticks every 1 unit (5 minor ticks) in the Y axis
yticks(0.2, 5)
```
