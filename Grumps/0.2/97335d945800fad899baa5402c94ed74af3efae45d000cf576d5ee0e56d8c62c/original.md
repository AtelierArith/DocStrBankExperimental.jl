```
Save( fn, mt, sol :: GrumpsSolution; keywords... )
```

Saves the solution stored in `sol` to a file with filename `fn` which has mime type `mt`.  

There are several keywords that are described below, some of which will be ignored for some mime types.  Allowed mime types are `text/plain`, `text/csv`, and `text/tex`.

| Keyword            | Description         | Default |
|:------------------ |:------------------- |:------- |
| `colsep`           | column separator    | `","`   |
| `adorned`          | make output pretty? | `true`  |
| `printθ`           | print θ results?    | `true`  |
| `printβ`           | print β results?    | `true`  |
| `printδ`           | print δ results?    | `false` |
| `printconvergence` | convergence stats?  | `true`  |
