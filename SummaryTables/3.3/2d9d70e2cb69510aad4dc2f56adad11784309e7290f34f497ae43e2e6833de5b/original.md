```
Styled(value; color, bold, italic, underline)
```

Create a `Styled` object wrapping `value` which renders `value` formatted according to these optional properties:

  * `bold::Union{Nothing,Bool}`
  * `italic::Union{Nothing,Bool}`
  * `underline::Union{Nothing,Bool}`
  * `color::Union{Nothing,String}` The text color as a hex RGB string like #FA03C7.  Note that you need to add `\usepackage{xcolor}` to use colored text in LaTeX.
