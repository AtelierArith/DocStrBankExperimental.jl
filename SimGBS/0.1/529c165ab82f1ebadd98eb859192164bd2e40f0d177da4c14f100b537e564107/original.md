```
definePopulation(numFounders, endSize, numGenCha, numGenCon, numGenFinal, numInd, useWeights, usePedigree, pedFile, pedOutput);
```

Create population structure for simulation.

This function generates different population structure, and there is an option to follow a user-defined pedigree.

# Arguments

  * `numFounders`: number of founders in the base population
  * `endSize`: number of individuals to end up in the changingPopSize step
  * `numInd`: number of individuals to be simulated
  * `numGenCha`: number of generations for changingPopSize function
  * `numGenCon`: number of generations for constantPopSize function
  * `numGenFinal`: number of final generations to be used to select individual
  * `useWeights`: weights of each contributing genetarion in the final population composition
  * `usePedigree`: set to false if you don't use pedigree, otherwise specify the pedigree file to be used
  * `pedFile`: pedigree file
  * `pedOutput`: set to true if return pedigree output

# Notes

  * Please consider modifyin the combination of constant and changing population (as well as combining multiple populations) when defining complicated population structure.

# Examples

```julia
julia> definePopulation(100, 500, 20, 100, 4, 96,  Array{Float64}(undef,0), false, "sim.ped", false);
```
