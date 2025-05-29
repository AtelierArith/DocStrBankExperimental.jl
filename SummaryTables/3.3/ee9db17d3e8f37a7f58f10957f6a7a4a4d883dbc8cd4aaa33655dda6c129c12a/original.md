```
Cell(value, style::CellStyle)
Cell(value; [bold, italic, underline, halign, valign, border_bottom, indent_pt, merge, mergegroup])
```

Construct a `Cell` with value `value` and `CellStyle` `style`, which can also be created implicitly with keyword arguments. For explanations of the styling options, refer to `CellStyle`. A cell with value `nothing` is displayed as an empty cell (styles might still apply). The type of `value` can be anything.

Some types with special behavior are:

  * `Multiline` for content broken over multiple lines in a cell. This object may not be used nested in other values, only as the top-level value.
  * `Concat` for stringing together multiple values without having to interpolate them into a `String`, which keeps their own special behaviors intact.
  * `Superscript` and `Subscript`
  * `Annotated` for a value with an optional superscript label and a footnote annotation.
