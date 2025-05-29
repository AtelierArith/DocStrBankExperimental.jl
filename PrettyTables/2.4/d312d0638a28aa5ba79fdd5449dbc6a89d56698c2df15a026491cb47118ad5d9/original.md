```
abstract type CustomTextCell
```

Abstract type of custom cells in the text backend.

Each type must implement the following API:

  * `get_printable_cell_text`: A function that must return a vector of strings with the   printable text, *i.e.* without any non-printable character.
  * `get_rendered_line`: A function that must return the rendered line that will be printed to   the display.
  * `apply_line_padding!`: Apply a certain number of spaces to the left and right of a   specific line.
  * `crop_line!`: A function that must crop a certain number of printable characters from the   end of the line.
  * `append_suffix_to_line!`: Append a string suffix to a line of the custom cell.
  * `apply_line_padding!`: Apply left and right padding to a line of the custom cell.
  * `crop_line!`: Crop a certain number of characters from a line of the custom cell.
  * `get_printable_cell_line`: Get a printable line of the custom cell.
  * `get_rendered_line`: Get a rendered line of the custom cell.
  * `parse_cell_text`: Parse the cell text and return a `Vector{String}` with the printable   lines.
  * `reset!`: Reset all the temporary fields. This function is not required.
