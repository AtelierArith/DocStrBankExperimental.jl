```
str_c(strings::AbstractVector; sep::AbstractString="")
```

Joins a vector of strings into a single string.

Arguments

  * `strings`: Input strings.
  * `sep`: The separator between the strings. Default is an empty string.
  * `collapse` : If provided, it joins the concatenated strings with the specified collapse string. If not, it returns an array of the concatenated strings.

Returns The joined string.

Examples

```jldoctest
julia> str_c(["apple", "banana", "pear", "pineapple"])
"applebananapearpineapple"

julia> str_c(["Michigan", "Maryland"] , ["MI", "MD"], sep = ", ")
2-element Vector{String}:
 "Michigan, MI"
 "Maryland, MD"

julia> str_c(["Michigan", "Maryland"] , ["MI", "MD"], sep = ", ", collapse =  ";   ")
"Michigan, MI;   Maryland, MD"
```
