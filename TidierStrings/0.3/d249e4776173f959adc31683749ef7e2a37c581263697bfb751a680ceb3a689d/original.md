```
str_replace_all(String::String, pattern::Union{String, Regex}, replacement::String)
```

Replace all occurrences of a pattern in a string with a specified string.

# Arguments

  * `string`: The string in which to replace the pattern.
  * `pattern`: A string or a regular expression to find within the string.

replacement: The string to insert in place of the pattern. The pattern can include special logic:

Use | to represent "or" (e.g., "red|blue" matches any string that contains "red" or "blue"). Returns A new string with all occurrences of the pattern replaced with the replacement.

# Examples

```jldoctest
julia> str_replace_all("I Think You Should Leave is a great show", " ", "")
"IThinkYouShouldLeaveisagreatshow"

julia> str_replace_all("The blue sky is blue", "blue", "red")
"The red sky is red"

julia> str_replace_all("The blue sky is blue", r"blu", "red")
"The blue sky is blue"

julia> str_replace_all("The blue sky is blue", "blue|sky", "red")
"The red red is red"
```
