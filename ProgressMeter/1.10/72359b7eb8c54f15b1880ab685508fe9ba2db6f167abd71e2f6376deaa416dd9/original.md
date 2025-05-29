```
next!(p::Union{Progress, ProgressUnknown}; step::Int = 1, options...)
```

Report that `step` units of progress have been made. Depending on the time interval since the last update, this may or may not result in a change to the display.

You may optionally change the `color` of the display. See also `update!`.
