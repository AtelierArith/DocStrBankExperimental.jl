```
get_sections
```

Separate a whole parsed Markdown document into blocks of the text between headers. 

# Arguments

  * `contents`: The `Vector` of content structs of a MD struct from Julia standard library `Markdown.parse`
  * `headers`: Vector of `Header` structs that are found in the submitted document

# Keyword Arguments

  * `name_sections = true`: boolean setting to get a dictionary instead of a vector.

# Returns

  * By default, a dictionary of the headers first word as key and the sections between the headers
  * A Vector of all section texts between the headers of the document
