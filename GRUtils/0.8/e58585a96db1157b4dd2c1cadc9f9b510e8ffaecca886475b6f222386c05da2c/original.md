```
xticklabels(f)
yticklabels(f)
```

Customize the string of the X and Y axes tick labels.

The labels of the tick axis can be defined by a function with one argument (the numeric value of the tick position) that returns a string, or by an array of strings that are located sequentially at X = 1, 2, etc.

Use the keyword argument `xticklabels=s`, etc. in plotting functions, to set the axis tick labels during the creation of plots.

# Examples

```julia
# Label the range (0-1) of the Y-axis as percent values
yticklabels(p -> Base.Printf.@sprintf("%0.0f%%", 100p))
# Label the X-axis with a sequence of strings
xticklabels(["first", "second", "third"])
```
