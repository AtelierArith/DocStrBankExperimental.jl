```julia
function importdataset(filepath, [delim];
    	importas=:Dict,
    	elements=nothing,
    	standardize::Bool=true,
    	floattype=Float64,
    	skipstart::Integer=0,
    	skipnameless::Bool=true,
    	mindefinedcolumns::Integer=0
)
```

Import a delimited file specified by `filepath` with delimiter `delim` as a dataset in the form of either a `Dict` or a `NamedTuple`.

Possible keyword arguments include:

```
	importas
```

Specify the format of the imported dataset. Options include `:Dict` and `:Tuple`

```
	elements
```

Specify the names to be used for each element (i.e., column) of the dataset. Default value (`nothing`) will cause `elements` to be read from the first row of the file

```
	standardize
```

Convert columns to uniform type wherever possible. Boolean; `true` by default.

```
	floattype
```

Preferred floating-point type for numerical data. `Float64` by default.

```
	skipstart
```

Ignore this many rows at the start of the input file (useful if input file has a header or other text before the column names). `0` by default.

```
	skipnameless
```

Skip columns with no column name. Boolean; `true` by default

```
	mindefinedcolumns
```

Skip rows with fewer than this number of delimiters. `0` by default.
