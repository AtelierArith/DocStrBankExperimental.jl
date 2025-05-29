```
network_expectedCF_formulas(network::HybridNetwork; 
                            showprogressbar=true, 
                            inheritancecorrelation=0, 
                            filename="symbolicQNC-HFO-out"::AbstractString, 
                            symbolic=false::Bool, 
                            savecsv=false::Bool, 
                            macaulay=false::Bool, 
                            matlab=false::Bool, 
                            multigraded=false::Bool)
```

Compute expected concordance factors (CFs) for quartets in a phylogenetic network, optionally generating symbolic formulas.

This function calculates the expected concordance factors (CFs) for all possible quartets of taxa in a `HybridNetwork`,  taking into account coalescent processes and inheritance correlations at hybrid nodes. It can operate in numerical mode  (default) or symbolic mode (when `symbolic=true`), where it expresses CFs as formulas involving branch lengths and  inheritance parameters (γ). Results are logged to a file, and optional outputs can be saved as CSV, Macaulay2, MATLAB,  or multigraded implicitization files for further analysis.

# Arguments

  * `network::HybridNetwork`: A phylogenetic network from the PhyloNetworks package, with edge lengths in coalescent units and γ values for hybrid edges.
  * `showprogressbar::Bool=true`: If true, displays a progress bar for quartet calculations.
  * `inheritancecorrelation::Number=0`: Correlation between inheritance probabilities at hybrid nodes (must be between 0 and 1).
  * `filename::AbstractString="symbolicQNC_HFO_out"`: Base name for output files (e.g., log, CSV, Macaulay2, MATLAB).
  * `symbolic::Bool=false`: If true, computes CFs as symbolic expressions; requires all edge parameters to be defined or assigns random values.
  * `savecsv::Bool=false`: If true, saves CFs to a CSV file named `<filename>.csv`.
  * `macaulay::Bool=false`: If true, generates a Macaulay2 script (`<filename>.m2.txt`) for symbolic analysis; requires `symbolic=true`.
  * `matlab::Bool=false`: If true, generates a MATLAB script (`<filename>.m`) for symbolic analysis; requires `symbolic=true`.
  * `multigraded::Bool=false`: If true, generates a Macaulay2 multigraded implicitization script (`<filename>.im.m2.txt`); requires `symbolic=true`.

# Returns

  * `quartet::Vector{PhyloNetworks.QuartetT}`: Array of QuartetT objects containing quartet indices, taxa, and CFs (numerical or symbolic).
  * `taxa::Vector{String}`: Sorted list of taxon names from the network.

# Throws

  * `ErrorException`: If the root is a leaf, edge lengths are missing/negative, γ values are missing/negative, or inheritance correlation is invalid.
  * `ErrorException`: If `macaulay` or `matlab` is true but `symbolic` is false.

# Side Effects

  * Writes a log file (`<filename>.log`) with topology, parameters, and CFs.
  * Optionally writes CSV, Macaulay2, MATLAB, or multigraded files based on flags.
