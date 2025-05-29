```
HtmlHighlighter
```

Defines the default highlighter of a table when using the html backend.

# Fields

  * `f::Function`: Function with the signature `f(data,i,j)` in which should return `true` if   the element `(i,j)` in `data` must be highlighter, or `false` otherwise.
  * `fd::Function`: Function with the signature `f(h,data,i,j)` in which `h` is the   highlighter. This function must return the `HtmlDecoration` to be applied to the cell   that must be highlighted.
  * `decoration::HtmlDecoration`: The `HtmlDecoration` to be applied to the highlighted cell   if the default `fd` is used.

# Remarks

This structure can be constructed using two helpers:

```
HtmlHighlighter(f::Function, decoration::HtmlDecoration)

HtmlHighlighter(f::Function, fd::Function)
```

The first will apply a fixed decoration to the highlighted cell specified in `decoration` whereas the second let the user select the desired decoration by specifying the function `fd`.
