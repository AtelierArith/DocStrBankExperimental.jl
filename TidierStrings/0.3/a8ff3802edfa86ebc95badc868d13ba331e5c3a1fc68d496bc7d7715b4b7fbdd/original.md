```
str_like(string, pattern::String; ignore_case::Bool = true)
```

Detect a pattern in each string of the input vector using SQL-like pattern matching.

Arguments

  * `string`: Input string.
  * `pattern`: The pattern to check for. Can be a string or a regular expression.
  * `ignore_case`: Whether to ignore case when matching. Default is `true`.

Returns A vector of booleans indicating if the string matches the pattern.

```jldoctest
julia> str_like("hello", "h_llo")
true

julia> str_like.(["Hello", "world", "HELLO", "WORLD"], "H_llo")
4-element BitVector:
 1
 0
 1
 0
```
