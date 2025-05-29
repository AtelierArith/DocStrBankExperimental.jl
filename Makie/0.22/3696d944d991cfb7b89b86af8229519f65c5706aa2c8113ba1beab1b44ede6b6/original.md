```
Linestyle(value::Vector{<:Real})
```

A type that can be used as value for the `linestyle` keyword argument of plotting functions to arbitrarily customize the linestyle.

The `value` is a vector specifying the boundaries of the dashes in the line. Values 1 and 2 demarcate the first dash, values 2 and 3 the first gap, and so on. This means that usually, a pattern should have an odd number of values so that there's always a gap after a dash.

Here's an example in ASCII code. If we specify `[0, 3, 6, 11, 16]` then we get the following pattern:

```
#  0  3   6   11   16  3  6   11
#   ---   -----     ---   -----
```
