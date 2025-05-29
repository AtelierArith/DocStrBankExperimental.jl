```julia
to_html_content(expr)
```

Create `HTMLContent` from a DSL expression. Assumes `divv` generates a string of HTML from `expr` based on your DSL.

## Arguments

  * `expr`: The DSL expression to be converted to HTML.

## Returns

  * An instance of `HTMLContent` containing the generated HTML string.

## Example

```julia
html_expr = divv(
    head(
        title("Hello, World!")
    ),
    body(
        h1("Hello, World!")
    )
)
html_content = to_html_content(html_expr)
```
