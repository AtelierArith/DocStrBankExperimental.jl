```
textview([io::IO,] text::AbstractString, view::NTuple{4, Int}; kwargs...)
textview([io::IO,] lines::Vector{AbstractString}, view::NTuple{4, Int}; kwargs...)
```

Create a view of `text` or `lines` considering a `view` configuration. The latter is a tuple with four integers that has the following meaning:

  * Top line;
  * Number of lines;
  * Left column; and
  * Number of columns.

If a value equal or lower than 0 is passed to any of those options, its extreme value is used.

# Keywords

  * `active_highlight::String`: ANSI escape sequence that contains the decoration of the   active highlight. (**Default** = `\e[30;43m`)
  * `active_match::Int`: The match number that is considered active. This match is highlighted   using `active_highlight` instead of `highlight`.  (**Default** = 0)
  * `frozen_columns_at_beginning::Int`: Number of frozen columns that are drawn in the   beginning. (**Default** = 0)
  * `frozen_lines_at_beginning::Int`: Number of frozen lines that are drawn in the beginning.   (**Default** = 0)
  * `highlight::String`: ANSI escape sequence that contains the decoration of the highlight.   (**Default** = `\e[7m`)
  * `maximum_number_of_columns::Int`: Maximum number of columns in the view, regardless the   view width. If it is -1, the entire view width will be used. (**Default** = -1)
  * `maximum_number_of_lines::Int`: Maximum number of lines in the view, regardless the view   height. If it is -1, the entire view height will be used. (**Default** = -1)
  * `parse_decorations_before_view::Bool`: If `true`, we will scan all the decorations in the   lines before the view and consider them when rendering the output. Otherwise, everything   before the beginning of the view will be discarded. If this option is `false`, the   decoration can be wrong. However, this feature can require a high amount of processing   depending on the input string size and the view position. (**Default** = `false`)
  * `ruler_decoration::String`: ANSI escape sequence that contains the decoration of the   ruler. (**Default** = `\e[90m`)
  * `show_ruler::Bool`: If `true`, a ruler with the row numbers will be shown to the left of   the view. (**Default** = `false`)
  * `visual_lines::Union{Nothing, Vector{Int}}`: Vector containing the number of the lines   that will be highlighted with a different background (visual mode). If it is `nothing`,   no line will be changed. (**Default** = `nothing`)
  * `visual_line_backgrounds::Union{String, Vector{String}}`: ANSI code for the background   decorations of the lines in `visual_lines`. It can be a `Vector{String}`, where a   background can be specified for each line, or a `String`, where all backgrounds will   have the same decoration. (**Default** = "44")
  * `title_lines::Int`: Number of lines at the beginning of the text to be considered as   title, meaning that they will be printed statically on the screen regardless the view.   (**Default** = 0)

If `text::AbstractString` is passed, the following keyword is available:

  * `search_regex::Uniont{Nothing, Regex}`: A regex used to highlight matches in the text   view. (**Default** = `nothing`).

If `lines::Vector{AbstractString}` is passed, the following keyword is available:

  * `search_matches::Union{Nothing, Dict{Int, Vector{Tuple{Int, Int}}}}`: The search matches   that are highlighted in the text view. This dictionary must be created using the   function [`string_search_per_line`](@ref). (**Default** = `nothing`)

# Returns

If `io` is passed, the view is written to it and the function returns:

  * `Int`: Number of cropped lines at the end.
  * `Int`: Maximum number cropped characters in a row.

However, if `io` is not passed, the function returns:

  * `String`: Text view.
  * `Int`: Number of cropped lines at the end.
  * `Int`: Maximum number cropped characters in a row.

!!! note
    If only frozen lines are printed, the second returned value is set to 0.

    If only frozen columns are printed, the third returned value is set to 0.

