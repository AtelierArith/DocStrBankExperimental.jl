```
Facet(; [row], , [column], kw...)
Facet(field; columns::Int=nothing, kw...)
```

Creates a `FacetSpec` for a facet specification. [](https://vega.github.io/vega-lite/docs/facet.html). A `field` can be passed as a positional argument, or must be passed in the `row`/`column` keyword argument.

# Examples

```
Facet("site:O", columns=2, sort=(op=:median, field=:yield))
Facet(row="Origin:N)
```
