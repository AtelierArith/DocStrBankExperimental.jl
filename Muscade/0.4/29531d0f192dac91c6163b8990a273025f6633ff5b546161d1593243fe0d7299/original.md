```
matrix = studysingular(state;SP,[iclasses=(Λ,:X,:U,:A)],[jclasses=iclasses],[verbose::𝕓=true],[dbg=(;)])
```

Generates an incremental matrix for `state` (no time derivatives) corresponding to the classes required,  and report on the null space of the matrix.

To do so, the incremental matrix is converted to full format, limiting the applicability to small models.

The function returns the incremental matrix.
