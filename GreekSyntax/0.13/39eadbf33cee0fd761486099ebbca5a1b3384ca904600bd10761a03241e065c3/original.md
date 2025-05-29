Compose HTML string for the annotated sentence `sa` indented by level of subordination. Formatting relies on data from a vector of token annotations and annotations on verbal units.

```julia
htmltext_indented(
    sa,
    groups,
    tknannotations;
    sov,
    vucolor,
    palette,
    syntaxtips,
    connectorids
)

```
