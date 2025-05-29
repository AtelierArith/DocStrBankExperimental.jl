```
struct TextFormat
```

# Fields

  * `up_right_corner::Char`: Character in the up right corner.
  * `up_left_corner::Char`: Character in the up left corner.
  * `bottom_left_corner::Char`: Character in the bottom left corner.
  * `bottom_right_corner::Char`: Character in the bottom right corner.
  * `up_intersection::Char`: Character in the intersection of lines in the up part.
  * `left_intersection::Char`: Character in the intersection of lines in the left part.
  * `right_intersection::Char`: Character in the intersection of lines in the right part.
  * `middle_intersection::Char`: Character in the intersection of lines in the middle of the   table.
  * `bottom_intersection::Char`: Character in the intersection of the lines in the bottom   part.
  * `column::Char`: Character in a vertical line inside the table.
  * `row::Char`: Character in a horizontal line inside the table.
  * `hlines::Vector{Symbol}`: Horizontal lines that must be drawn by default.
  * `vlines::Union{Symbol, Vector{Symbol}}`: Vertical lines that must be drawn by default.

# Pre-defined formats

The following pre-defined formats are available: `unicode` (**default**), `mysql`, `compact`, `markdown`, `simple`, `ascii_rounded`, and `ascii_dots`.
