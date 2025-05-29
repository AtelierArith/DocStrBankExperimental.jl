```
test_vue_parsing(html_string; prettify::Bool = true, level = 0, indent = 4, context = @__MODULE__)
```

Parse html code with automatic line breaks and indentingto Julia/StippleUI code, execute the code and prettify the result. Indenting can be determined by

  * `level`: starting level for formatting; negative values are allowed, negative levels are not indented
  * `indent`: either Integer for number of ' ' characters per level or a string value
  * `context`: context for evaluation
