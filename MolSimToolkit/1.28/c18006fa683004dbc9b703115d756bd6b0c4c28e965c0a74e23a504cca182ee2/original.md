```
remd_data(log::String)
```

Function to read the log file from a (H)REMD simulation performed with Gromacs.

Returns a `GromacsREMDlog` structure, containing the steps at which the exchange was tried, the exchange matrix and the probability matrix. The exchange matrix contains the replica number at each level of perturbation for each step. The probability matrix contains the probability of finding each replica at each level.

Tested with log files of Gromacs versions:      - 2019.4     - 5.0.4

# Example

First obtaina the REMD data from the log file:

```julia-repl
julia> using MolSimToolkit

julia> data = remd_data(MolSimToolkit.gmx2019_9_log)
```

Then plot the exchange matrix, which will provide a visual inspection of the exchange process:

```julia-repl
julia> using Plots

julia> heatmap(data) 
```
