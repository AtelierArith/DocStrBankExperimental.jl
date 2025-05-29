Compose HTML string for the annotated sentence `sa` using data from a vector of token annotations.  Boolean flags for `sov` and `vucolor` provoke CSS additions for Subject-Object-Verb highlight, and for color coding by verbal unit.

```julia
htmltext(
    sa,
    tknannotations;
    sov,
    vucolor,
    colors,
    syntaxtips,
    connectorids
)

```
