```
maximum_adjacency_visit(g[, distmx][, log][, io])
```

Return the vertices in `g` traversed by maximum adjacency search. An optional `distmx` matrix may be specified; if omitted, edge distances are assumed to be 1. If `log` (default `false`) is `true`, visitor events will be printed to `io`, which defaults to `STDOUT`; otherwise, no event information will be displayed.
