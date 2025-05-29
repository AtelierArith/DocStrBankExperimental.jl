```
fread(file::AbstractString; header=true, kw...)
```

# Arguments

  * `file`: the csv file to read
  * `header`: whether the csv file has header?
  * `kw`: other parameters for `CSV.File`

# Examaple

```
fread("a.csv")
```
