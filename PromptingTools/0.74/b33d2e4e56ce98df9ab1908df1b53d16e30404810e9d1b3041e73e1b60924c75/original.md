```
pprint(io::IO, msg::AbstractMessage; text_width::Int = displaysize(io)[2])
```

Pretty print a single `AbstractMessage` to the given IO stream.

`text_width` is the width of the text to be displayed. If not provided, it defaults to the width of the given IO stream and add `newline` separators as needed.
