```
importcsv(filepath::String, interface::Interface; delimiter = ',', header = false, comment = "Imported from csv file", savelog = true, kwargs...)
```

Import function for raw data to be transformed to stress and strain using an `Interface`. Column numbers in the csv containging the force/displacement data need to be indicated as keyword arguments using the corresponding symbols in the `interface`..

# Examples

```julia-repl
julia> importcsv("myfile.csv", AFM(2e-6), t=1, d=2, f=3)
```
