Generate Table of Contents using Markdown cells. Headers h1-h6 are used. 

# Keyword arguments:

`title` header to this element, defaults to "Table of Contents"

`indent` flag indicating whether to vertically align elements by hierarchy

`depth` value to limit the header elements, should be in range 1 to 6 (default = 3)

`aside` fix the element to right of page, defaults to true

`include_definitions` add cells that start with docstrings to the ToC, defaults to false

# Examples:

```julia
TableOfContents()

TableOfContents(title="Experiments 🔬")

TableOfContents(title="📚 Table of Contents", indent=true, depth=4, aside=true)
```
