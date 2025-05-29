```
struct LatexTableFormat
```

This structure defines the format of the LaTeX table.

# Fields

  * `top_line::String`: Top line of the table.
  * `header_line::String`: Line that separate the header from the table body.
  * `mid_line::String`: Line printed in the middle of the table.
  * `bottom_line::String`: Bottom line of the table.
  * `left_vline::String`: Left vertical line of the table.
  * `mid_vline::String`: Vertical line in the middle of the table.
  * `right_vline::String`: Right vertical line of the table.
  * `header_envs::Vector{String}`: LaTeX environments that will be used in each header cell.
  * `subheader_envs::Vector{String}`: LaTeX environments that will be used in each sub-header   cell.
  * `hlines::Vector{Symbol}`: Horizontal lines that must be drawn by default.
  * `vlines::Union{Symbol, Vector{Symbol}}`: Vertical lines that must be drawn by default.
  * `table_type::Symbol`: Select the type of table that should be used for this format.
  * `wrap_table::Bool`: Select if the table must be wrapped inside the environment defined by   `wrap_table_environment`.
  * `wrap_table_environment::String`: Environment in which the table will be wrapped if   `wrap_table` is true.
