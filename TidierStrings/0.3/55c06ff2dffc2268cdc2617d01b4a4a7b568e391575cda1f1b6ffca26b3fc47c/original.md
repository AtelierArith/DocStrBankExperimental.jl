```
str_wrap(string::AbstractString; width::Integer=80, indent::Integer=0, exdent::Integer=0, whitespace_only::Bool=true)::String
```

Wraps a string into multiple lines.

Arguments

  * `string`: Input string.
  * `width`: The maximum width of each line. Default is 80.
  * `indent`: The number of spaces to indent each line. Default is 0.
  * `exdent`: The number of spaces to exdent each line. Default is 0.
  * `whitespace_only`: Whether to only wrap on whitespace. Default is true.

Returns The wrapped string.

Examples

```jldoctest
julia> println(str_wrap("This is an example text that should be wrapped based on the given width and breaking rules.", width=20))
This is an example
text that should be
wrapped based on the
given width and
breaking rules.
```
