```
prettify(html::AbstractString; level::Int = 0, indent::Union{String, Int} = 4)
```

Format html code with automatic line breaks and indenting. Indenting can be determined by

  * level: starting level for formatting; negative values are allowed, negative levels are not indented
  * indent: either Integer for number of ' ' characters per level or a string value
