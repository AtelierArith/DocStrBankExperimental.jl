```
reshape_text(text, width::Int)
```

Reshape a string to be a multi-line text with given width.

Arguments:     text::AbstractString     width::Int

New line characters `` are inserted to give a new string in which each line has is at most `width` wide. This takes into account  characters with width > 1 and number of code units > 1. New lines are preferentially insterted at spaces if there is any near the end of the line to improve readability.
