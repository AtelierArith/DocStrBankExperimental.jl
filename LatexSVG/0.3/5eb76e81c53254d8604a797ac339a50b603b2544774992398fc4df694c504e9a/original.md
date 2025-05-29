```
Lsvg"..."
```

Renders the input as SVG with the current preamble and LaTeX engine.

Similar to `raw"..."` strings, you do not have to escape special characters like `\` and `$`, which makes it easier to write LaTeX.

You can interpolate variables using the `%$` syntax, which is the same as the `L"..."` string macro in `LaTeXStrings.jl`. For instance, if there is a variable `x = 10`, then `Lsvg"number %$x"` renders the string `"number 10"`. However, unlike the `L"..."` macro, `Lsvg"..."` does not automatically wrap your input in a pair of dollar signs, since it is very much possible that you'll want to use some other LaTeX environments.
