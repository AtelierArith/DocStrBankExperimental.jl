```
parse_vue_html(html, level = 0; indent::Union{String, Int} = 4, vec_sep::String = ",
```

", context = @**MODULE**)

Parse html code to Julia/StippleUI code with automatic line breaks and indenting. Indenting can be determined by

  * `level: starting level for formatting; negative values are allowed, negative levels are not indented
  * `indent`: either Integer for number of ' ' characters per level or a string value
  * `vec_sep`: separator in array listings, reasonable values are `",\n"`, `"\n\n"`, `",\n\n"`
  * `context`: context for evaluation
