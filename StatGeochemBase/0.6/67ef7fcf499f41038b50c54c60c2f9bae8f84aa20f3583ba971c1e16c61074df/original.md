```julia
exportdataset(dataset, [elements], filepath, delim;
    	floatout::Bool=false,
    	findnumeric::Bool=false,
    	skipnan::Bool=true,
    	digits::Integer,
    	sigdigits::Integer
    	rows=:
)
```

Convert a dict or named tuple of vectors into a 2-D array with variables as columns Export a `dataset` (in the form of either a `Dict` or a `NamedTuple`), optionally specifying which `elements` to export, as a delimited ASCII text file with the name specified by `filepath` and delimiter `delim`.

Possible keyword arguments include:

```
	digits
	sigdigits
```

Specify a number of absolute or significant digits to which to round the printed output. Default is no rounding.

```
	skipnan
```

Leave `NaN`s as empty cells in the delimited output file. Boolean; `true` by default.

```
	floatout
```

Force all output to be represented as a floating-point number, or else `NaN`. Boolean; `false` by default.

```
	findnumeric
```

Export only numeric columns. Boolean; `false` by default.

```
	rows
```

specify which rows of the dataset to export. Default `:` exports all rows.
