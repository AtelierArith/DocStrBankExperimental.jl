```
digestGenome(genofile, re, useChr, useChrLen, lower ,upper, plotOutput, writeOutput)
```

Perform virtual digestion using restriction enzyme and generate GBS fragments.

This function uses specified restriction enzyme(s) to digest genome and therefore generate GBS fragments. Fragment size-selection step is also included.

# Arguments

  * `genofile`: file containing the reference genome
  * `re`: restriction enzyme(s) to be used
  * `useChr`: either the number of chromosome or a set of chromosome(s) to be simulated
  * `useChrLen`: length of chromosome in cM to be used in simulation, otherwise using entire chromosome
  * `lower`: lower threshold of fragment size-selection
  * `upper`: upper threshold of fragment size-selection
  * `winSize`: size of window used for calculating average genomic coverage
  * `plotOutput`: set to true if graphical outputs are required
  * `writeOutput`: set to true if text outputs are required

...

# Examples

```julia
julia> digestGenome("ref.fa.gz", [SimGBS.ApeKI], [1], Array{Float64}(undef,0), 65 ,195, 1000000, false, true)
```
