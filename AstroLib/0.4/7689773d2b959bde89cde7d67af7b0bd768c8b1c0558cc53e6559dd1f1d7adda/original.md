```
ten(deg[, min, sec]) -> decimal
ten("deg:min:sec") -> decimal
```

### Purpose

Converts a sexagesimal number or string to decimal.

### Explanation

`ten` is the inverse of the `sixty` function.

### Arguments

`ten` takes as argument either three scalars (`deg`, `min`, `sec`) or a string. The string should have the form `"deg:min:sec"` or `"deg min sec"`.  Also any iterable like `(deg, min, sec)` or `[deg, min, sec]` is accepted as argument.

If minutes and seconds are not specified they default to zero.

### Output

The decimal conversion of the sexagesimal numbers provided is returned.

### Method

The formula used for the conversion is

$$
\mathrm{sign}(\mathrm{deg})·\left(|\mathrm{deg}| + \frac{\mathrm{min}}{60} + \frac{\mathrm{sec}}{3600}\right)
$$

### Example

```jldoctest
julia> using AstroLib

julia> ten(-0.0, 19, 47)
-0.3297222222222222

julia> ten("+5:14:58")
5.249444444444444

julia> ten("-10 26")
-10.433333333333334

julia> ten((-10, 26))
-10.433333333333334
```

### Notes

These functions cannot deal with `-0` (negative integer zero) in numeric input. If it is important to give sense to negative zero, you can either make sure to pass a floating point negative zero `-0.0` (this is the best option), or use negative minutes and seconds, or non-integer negative degrees and minutes.
