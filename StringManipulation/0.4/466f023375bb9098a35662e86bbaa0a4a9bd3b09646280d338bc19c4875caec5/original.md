```
printable_textwidth(str::AbstractString) -> Int
```

Return the text width of `str` considering only the printable characters, *i.e.* removing all ANSI escape sequences related to decorations.

!!! note
    Characters like `\n` and `\t` are treated as normal characters.

