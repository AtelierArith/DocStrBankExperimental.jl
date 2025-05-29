```
striprtf([out::IO,] text::AbstractString)
```

Given a string `text` in [Rich Text Format (RTF)](https://en.wikipedia.org/wiki/Rich_Text_Format), returns a string of "plain text" with all of the RTF formatting removed.

If the optional `out` argument is supplied, the output is instead written to this output `IO` stream, returning `out`.
