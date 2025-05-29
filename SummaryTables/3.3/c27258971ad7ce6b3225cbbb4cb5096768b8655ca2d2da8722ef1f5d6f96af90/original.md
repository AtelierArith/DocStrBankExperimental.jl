```
function Table(cells;
    header = nothing,
    footer = nothing,
    round_digits = 3,
    round_mode = :auto,
    trailing_zeros = false,
    footnotes = [],
    postprocess = [],
    rowgaps = Pair{Int,Float64}[],
    colgaps = Pair{Int,Float64}[],
    linebreak_footnotes = true,
)
```

Create a `Table` which can be rendered in multiple formats, such as HTML or LaTeX.

## Arguments

  * `cells::AbstractMatrix{<:Cell}`: The matrix of `Cell`s that make up the table.

## Keyword arguments

  * `header`: The index of the last row of the header, `nothing` if no header is specified.
  * `footer`: The index of the first row of the footer, `nothing` if no footer is specified.
  * `footnotes`: A vector of objects printed as footnotes that are not derived from `Annotated` values and therefore don't get labels with counterparts inside the table.
  * `round_digits = 3`: Float values will be rounded to this precision before printing.
  * `round_mode = :auto`: How the float values are rounded, options are `:auto`, `:digits` or `:sigdigits`. If `round_mode === nothing`, no rounding will be applied and `round_digits` and `trailing_zeros` will have no effect.
  * `trailing_zeros = false`: Controls if float values keep trailing zeros, for example `4.0` vs `4`.
  * `postprocess = []`: A list of post-processors which will be applied left to right to the table before displaying the table.  A post-processor can either work element-wise or on the whole table object. See the `postprocess_table` and  `postprocess_cell` functions for defining custom postprocessors.
  * `rowgaps = Pair{Int,Float64}[]`: A list of pairs `index => gap_pt`. For each pair, a visual gap   the size of `gap_pt` is added between the rows `index` and `index+1`.
  * `colgaps = Pair{Int,Float64}[]`: A list of pairs `index => gap_pt`. For each pair, a visual gap   the size of `gap_pt` is added between the columns `index` and `index+1`.
  * `linebreak_footnotes = true`: If `true`, each footnote and annotation starts on a separate line.

## Round mode

Consider the numbers `0.006789`, `23.4567`, `456.789` or `12345.0`.

Here is how these numbers are formatted with the different available rounding modes:

  * `:auto` rounds to `n` significant digits but doesn't zero out additional digits before the comma unlike `:sigdigits`. For example, `round_digits = 3` would result in `0.00679`, `23.5`, `457.0` or `12345.0`. Numbers at orders of magnitude >= 6 or <= -5 are displayed in exponential notation as in Julia.
  * `:digits` rounds to `n` digits after the comma and shows possibly multiple trailing zeros. For example, `round_digits = 3` would result in `0.007`, `23.457` or `456.789` or `12345.000`. Numbers are never shown with exponential notation.
  * `:sigdigits` rounds to `n` significant digits and zeros out additional digits before the comma unlike `:auto`. For example, `round_digits = 3` would result in `0.00679`, `23.5`, `457.0` or `12300.0`. Numbers at orders of magnitude >= 6 or <= -5 are displayed in exponential notation as in Julia.
