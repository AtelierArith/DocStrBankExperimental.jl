```
fcolor = FlameColors(n::Integer=2;
                     colorbg=colorant"white", colorfont=colorant"black",
                     colorsrt=colorant"crimson", colorsgc=colorant"orange")
```

Choose a set of colors for rendering a flame graph. There are several special colors:

  * `colorbg` is the background color
  * `colorfont` is used when annotating stackframes with text
  * `colorsrt` highlights [runtime dispatch](https://discourse.julialang.org/t/dynamic-dispatch/6963), typically a costly process
  * `colorsgc` highlights garbage-collection events

`n` specifies the number of "other" colors to choose when one of the above is not relevant. `FlameColors` chooses `2n` colors: the first `n` colors for odd depths in the stacktrace and the last `n` colors for even depths in the stacktrace. Consequently, different stackframes will typically be distinguishable from one another by color.

The highlighting can be disabled by passing `nothing` or a zero-element vector for `colorsrt` or `colorsgc`. When a single color is passed for `colorsrt` or `colorsgc`, this method generates four variant colors slightly different from the specified color. `colorsrt` or `colorsgc` can also be specified as multiple colors with a vector. The first half of the vector is for odd depths and the second half is for even depths. By using a one-element vector instead of a single color, the specified color is always used.

While the return value is a `struct`, it is callable and can be used as the `fcolor` input for `flamepixels`.
