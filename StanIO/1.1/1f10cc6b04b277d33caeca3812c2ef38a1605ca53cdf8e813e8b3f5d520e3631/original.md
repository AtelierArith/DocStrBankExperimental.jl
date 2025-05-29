```julia
parse_header(header)

```

Given a comma-separated list of names of Stan outputs, like that from the header row of a CSV file, parse it into a  (ordered) dictionary of `Variable` objects.

## Parameters

header::Vector{String}

```
Comma separated list of Stan variables, including index information.
For example, an `array[2] real foo` would be represented as
`..., foo.1, foo.2, ...` in Stan's .csv file.
```

## Returns

OrderedDict[String, Variable]

```
A dictionary mapping the base name of each variable to a struct `Variable`.
```

Exported.
