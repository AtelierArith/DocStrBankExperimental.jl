```
str_equal(string::String, pattern::Union{String, Regex})
```

Check if a string exactly equals to a pattern, or for regular expressions, if the pattern can match the entire string.

# Arguments

  * `string`: The string to be checked.
  * `pattern`: The pattern to compare against. Can be a plain string or a Regex.

Returns true if string equals to pattern (for plain strings) or if pattern can match the entire string (for Regex). false otherwise.

# Examples

```jldoctest
julia> str_equal("hello", "hello")
true
```
