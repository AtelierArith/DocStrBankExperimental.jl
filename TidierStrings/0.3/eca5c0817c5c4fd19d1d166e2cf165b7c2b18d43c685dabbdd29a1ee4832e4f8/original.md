```
str_detect(string::String, pattern::Union{String, Regex}; overlap::Bool=false)

                         Determine if a string contains a certain pattern.
```

# Arguments

  * `string`: The string to check.
  * `pattern`: A string or a regular expression to find within the string.
  * `overlap`: Whether the pattern can overlap (default false)

The pattern can include special logic:

```
                         Use | to represent "or" (e.g., "red|blue" matches any string that contains "red" or "blue").
                         Use & to represent "and" (e.g., "red&blue" matches any string that contains both "red" and "blue").
                         Returns
                         true if the string contains the pattern, false otherwise.
                         # Examples
                         ```jldoctest
                         julia> str_detect("The sky is blue", "blue")
                         true

                         julia> str_detect("The sky is blue", "red")
                         false

                         julia> str_detect("The sky is blue", r"blu")
                         false

                         julia> str_detect("The sky is blue", "blue|red")
                         true

                         julia> str_detect("The sky is blue and the sun is red", "blue&red")
                         true
                         ```
```
