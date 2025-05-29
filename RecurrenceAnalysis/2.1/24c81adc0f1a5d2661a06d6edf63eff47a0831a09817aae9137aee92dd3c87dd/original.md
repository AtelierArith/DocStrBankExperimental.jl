```
recurrenceplot([io,] R; minh = 25, maxh = 0.5, ascii, kwargs...) -> u
```

Create a text-based scatterplot representation of a recurrence matrix `R` to be displayed in `io` (by default `stdout`) using `UnicodePlots`. The matrix spans at minimum `minh` rows and at maximum `maxh*displaysize(io)[1]` (i.e. by default half the display). As we always try to plot in equal aspect ratio, if the width of the plot is even less, the minimum height is dictated by the width.

The keyword `ascii::Bool` can ensure that all elements of the plot are ASCII characters (`true`) or Unicode (`false`).

The rest of the `kwargs` are propagated into `UnicodePlots.scatterplot`.

Notice that the accuracy of this function drops drastically for matrices whose size is significantly bigger than the width and height of the display (assuming each index of the matrix is one character).
