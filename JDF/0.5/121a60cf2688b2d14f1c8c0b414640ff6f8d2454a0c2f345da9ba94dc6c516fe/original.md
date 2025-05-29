```
jdf"path/to/JDFfile.jdf"

JDFFile("path/to/JDFfile.jdf")
```

Define a JDF file, which you use with methods like  `names` and `size`.

## Example

using JDF, DataFrames df = DataFrame(a = 1:3, b = 1:3) savejdf(df, "plsdel.jdf")

names(jdf"plsdel.jdf") # [:a, :b] size(jdf"plsdel.jdf") # (2, 3)

size(jdf"plsdel.jdf", 1) # (2, 3)

size(jdf"plsdel.jdf", 1) # (2, 3)

# clean up

rm("plsdel.jdf", force = true, recursive = true)
