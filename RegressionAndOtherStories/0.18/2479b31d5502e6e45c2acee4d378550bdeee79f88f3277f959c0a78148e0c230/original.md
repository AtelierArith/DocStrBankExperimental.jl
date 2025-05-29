# ros_datadir()

Path to the RegressionAndOtherStories.jl data files.

Construct the path to a dataset in RegressionAndOtherStories.jl.

## Positional argument

```julia
* `parts::Vector{AbstractString}` # Path to data file in 
```

### Returns

```julia
* `path::AbstractString` # Path or "".
```

# Extended help

Examples:

```julia
ros_datadir("ElectionsEconomy", "hibbs.dat")
```

or, to read in as a DataFrame:

```julia
hibbs = CSV.read(ros_datadir("ElectionsEconomy", "hibbs.csv"), DataFrame)
```
