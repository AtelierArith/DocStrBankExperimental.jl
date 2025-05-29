# Method Stanmodel

Create a Stanmodel. 

### Constructors

```julia
Stanmodel(
  method=Sample();
  name="noname", 
  nchains=4,
  num_warmup=1000, 
  num_samples=1000,
  thin=1,
  model="",
  monitors=String[],
  random=Random(),
  output=Output(),
  printsummary=false,
  pdir::String=pwd(),
  tmpdir::String=joinpath(pwd(), "tmp"),
  output_format=:array
)

```

### Required arguments

```julia
* `method::Method`             : See ?Method
```

### Optional arguments

```julia
* `name::String`               : Name for the model
* `nchains::Int`               : Number of chains
* `num_warmup::Int`            : Number of samples used for num_warmup
* `num_samples::Int`           : Sample iterations
* `thin::Int`                  : Stan thinning factor
* `model::String`              : Stan program source
* `monitors::String[] `        : Variables saved for post-processing
* `random::Random`             : Random seed settings
* `output::Output`             : File output options
* `printsummary=true`          : Show computed stan summary
* `pdir::String`               : Working directory
* `tmpdir::String`             : Directory where output files are stored
* `output_format::Symbol `     : Output format
```

### CmdStan.jl supports 3 output_format values:

```julia
1. :array           # Returns an array of draws (default)
2. :mcmcchains      # Return an MCMCChains.Chains object
3. :dataframes      # Return an DataFrames.DataFrame object
4. :namedtuple      # Returns a NamedTuple object

The first option (the default) returns an Array{Float64, 3} with ndraws,
nvars, nchains as indices.

The 2nd option returns an MCMCChains.Chains object, the 3rd a DataFrame
object and the final option returns a NamedTuple.
```

### Example

```julia
stanmodel = Stanmodel(num_samples=1200, thin=2, name="bernoulli", 
  model=bernoullimodel);
```

### Related help

```julia
?stan                                  : Run a Stanmodel
?CmdStan.Sample                        : Sampling settings
?CmdStan.Method                        : List of available methods
?CmdStan.Output                        : Output file settings
?CmdStan.DataDict                      : Input data
?CmdStan.convert_a3d                   : Options for output formats
```
