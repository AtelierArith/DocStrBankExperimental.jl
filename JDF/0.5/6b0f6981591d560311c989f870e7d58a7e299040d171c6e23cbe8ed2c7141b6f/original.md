```
JDF.names(indir)
```

Load the column names associated with the JDF in `indir`

# Examples

```julia
using JDF, DataFrames
JDF.save(DataFrame(a = 1:3, b = 1:3), "plsdel.jdf")
JDF.names("plsdel.jdf")
```
