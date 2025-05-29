```
replace_default_background(str::AbstractString, new_background::AbstractString) -> String
```

Replace the default background in `str` by the one in `new_background`. The latter must be represented using a valid ANSI escape sequence that sets the background.

Internally, this function replaces the ANSI sequences that resets the decoration (`[0m`) and sets the default background (`[49m`) with the new background while keeping all the other supported decorations.
