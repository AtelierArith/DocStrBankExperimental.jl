```
pretty_stats(df; kwargs...)
```

Pretty-print a DataFrame using PrettyTables.

### Arguments

  * `io::IO`: an IO stream to which the table will be output (default: `stdout`);
  * `df::DataFrame`: the DataFrame to be displayed. If only certain columns of `df` should be displayed,     they should be extracted explicitly, e.g., by passing `df[!, [:col1, :col2, :col3]]`.

### Keyword Arguments

  * `col_formatters::Dict{Symbol, String}`: a Dict of format strings to apply to selected columns of `df`.     The keys of `col_formatters` should be symbols, so that specific formatting can be applied to specific columns.     By default, `default_formatters` is used, based on the column type.     If PrettyTables formatters are passed using the `formatters` keyword argument, they are applied     before those in `col_formatters`.
  * `hdr_override::Dict{Symbol, String}`: a Dict of those headers that should be displayed differently than     simply according to the column name (default: empty). Example: `Dict(:col1 => "column 1")`.

All other keyword arguments are passed directly to `pretty_table`. In particular,

  * use `tf=tf_markdown` to display a Markdown table;
  * do not use this function for LaTeX output; use `pretty_latex_stats` instead;
  * any PrettyTables highlighters can be given, but see the predefined `passfail_highlighter` and `gradient_highlighter`.
