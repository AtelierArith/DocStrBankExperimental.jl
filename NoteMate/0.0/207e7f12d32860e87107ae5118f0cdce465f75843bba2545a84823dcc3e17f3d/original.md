```
get_title_section
```

Get the sections that sit underneath title headers. 

# Arguments

  * `contents`: The `Vector` of content structs of a MD struct from Julia standard library `Markdown.parse`
  * `title_headers`: Vector of `Header` structs that are considered title headers

# Keyword Arguments

  * `name_sections = true`: boolean setting to get a dictionary instead of a vector.

# Returns

  * By default, a dictionary of the title section under the "Title" key
  * A Vector of all section texts started by title headers
