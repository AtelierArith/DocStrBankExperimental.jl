```
HrsePrintOptions(kwargs...)
```

Stores options for printing HRSE structures to text.

# Arguments

  * `indent = "  "`: The string to use for indentation.
  * `comments = true`: Whether to print comments from `CommentedElement` objects; if false, comments are ignored.
  * `extensions`: A collection of [`Extension`](@ref)s to HRSE.
  * `pairmode = COLON_MODE`: The [`PairMode`](@ref) to use when printing pairs.
  * `inlineprimitives = 20`: The maximum string length of a list of primitives to print on a single line instead of adding  a new indentation level.
  * `trailingnewline = true`: Whether to print a trailing newline at the end of the file.

See also [`writehrse`](@ref), [`ashrse`](@ref).
