```
update!(p::Union{Progress, ProgressUnknown}, [counter]; options...)
```

Set the progress counter to `counter`, relative to the `n` units of progress specified when `prog` was initialized.  Depending on the time interval since the last update, this may or may not result in a change to the display.

You may optionally change the color of the display. See also `next!`.
