```
CellStyle(;
    bold::Bool = false,
    italic::Bool = false,
    underline::Bool = false,
    halign::Symbol = :center,
    valign::Symbol = :top,
    indent_pt::Float64 = 0.0,
    border_bottom::Bool = false,
    merge::Bool = false,
    mergegroup::UInt8 = 0,
)
```

Create a `CellStyle` object which determines the visual appearance of `Cell`s.

Keyword arguments:

  * `bold` renders text `bold` if `true`.
  * `italic` renders text `italic` if `true`.
  * `underline` underlines text if `true`.
  * `halign` determines the horizontal alignment within the cell, either `:left`, `:center` or `:right`.
  * `valign` determines the vertical alignment within the cell, either `:top`, `:center` or `:bottom`.
  * `indent_pt` adds left indentation in points to the cell text.
  * `border_bottom` adds a bottom border to the cell if `true`.
  * `merge` causes adjacent cells which are `==` equal to be rendered as a single merged cell.
  * `mergegroup` is a number that can be used to differentiate between two otherwise equal adjacent groups of cells that should not be merged together.
