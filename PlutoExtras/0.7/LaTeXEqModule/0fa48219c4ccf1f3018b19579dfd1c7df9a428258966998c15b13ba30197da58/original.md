```
@texeq_str -> katex_html_code
```

Use to generate an HTML output that when rendered in Pluto shows latex equation using KaTeX.

Relies on [`texeq`](@ref) but avoids the need of double escaping backslashes.

# Examples

```julia
texeq"
\frac{q \sqrt{2}}{15} + 42
"
```
