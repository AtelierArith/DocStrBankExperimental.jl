```
ShowList
```

An `AbstractShow` wrapper type for showing iterables.  Note that, since the `ShowCases` module is intended primarily for creating `show` methods with output resembling Julia syntax, all iterables are shown as if they are of rank 1. Higher rank arrays should be shown with built-in methods or tools specifically intended for handling them.

Note that `ShowList` will show any element which is a `ShowEntry` object as is.  Therefore, one can pass it `ShowEntry` objects to override defaults only for specific entries.

## Constructors

  * `ShowList(o; brackets="()", left_bracket=Print("("), right_bracket=Print(")"),           new_lines=false, indent="    ", delim=Print(", "), max=8,           continuation=Print("…"), entry_style=nothing)`
  * `ShowList(o...; kw...)` (same keyword arguments as above)

## Arguments

  * `o`: Object or objects to be wrapped.  If only one is passed, it must be an iterable.
  * `brackets`: A string containing the brackets to be used (e.g. `"()", "[]", "{}", "''"`)
  * `left_bracket`: The left bracket to be shown.  By default, this will be computed from `brackets`.  If an argument is   given directly, it will be shown as is, i.e. use `Print("(")` to omit quotes.
  * `right_bracket`: The right bracket to be shown.  By default, this will be computed from `brackets`.  If an argument is   given directly, it will be shown as is, i.e. use `Print(")")` to omit quotes.
  * `new_lines::Bool`: Whether to print a new line for each entry.
  * `indent::AbstractString`: Indent to be used
  * `delim`: Delimiter to use for each entry.  This will be printed as is, so for example, use `Print(", ")` to get commas   with spacing.
  * `max::Integer`: the maximum number of entries to be printed.
  * `continuation`: object to print when `max` is hit.  Will be shown as is.

## Exmaples

```
julia> ShowList(1, 2)
(1, 2)

julia> ShowList(1, 2, new_lines=true)
(
    1,
    2
)

julia> ShowList(1, 2, max=1)
(1, …)

# pass ShowEntry objects to override defaults set by `ShowList`
julia> ShowList(ShowEntry("a", delim=Print(": "), new_line=true), 1, 2)
(
    "a": 1, 2)

```
