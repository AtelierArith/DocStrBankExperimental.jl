```
function rangeslider(vals::AbstractArray;
                value=medianelement(vals),
                label=nothing, readout=true,
                orientation="horizontal",
                direction="ltr", kwargs...)
```

Creates a slider widget which can take on the values in `vals` and accepts several "handles". Pass a vector to `value` with two values if you want to select a range. Use the `orientation="vertical"` keyword argument to create a vertical slider. By default the slider is top-to-botom and left-to-right, but this can be changed using the `direction="rtl"` keyword argument.
