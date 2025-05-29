```
Save( fn, sol :: GrumpsSolution; keywords... )
```

The same as the form of `Save` with prespecified mime type except that the mime type is now inferred from the file extension.  The keywords also have the same meaning, namely...

There are several keywords that are described below, some of which will be ignored for some mime types.  Allowed mime types are `text/plain`, `text/csv`, and `text/tex`.

| Keyword            | Description         | Default |
|:------------------ |:------------------- |:------- |
| `colsep`           | column separator    | `","`   |
| `adorned`          | make output pretty? | `true`  |
| `printθ`           | print θ results?    | `true`  |
| `printβ`           | print β results?    | `true`  |
| `printδ`           | print δ results?    | `false` |
| `printconvergence` | convergence stats?  | `true`  |
