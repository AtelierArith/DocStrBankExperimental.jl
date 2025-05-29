```
polytext(str::String, sty::PolyText.Style;
    scripting=false, linelimit=typemax(Int), verbose=false) where {T}
```

Renders the string `str` to a new coordinate system in a given style.

# Keyword args

  * `scripting`: boolean parameter for allocating special characters `^`, `_`, `{`, and `}`  for superscripting and subscripting. Follows the same usage as LaTeX.
  * `linelimit`: sets the maximum number of characters per line and continues on a new line  if `str` is longer than `linelimit`.
  * `verbose`: prints out information about the character dictionary.
