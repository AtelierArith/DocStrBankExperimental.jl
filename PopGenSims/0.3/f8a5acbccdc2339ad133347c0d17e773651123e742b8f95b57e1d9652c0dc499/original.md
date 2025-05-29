# Population genetics simulations

Repository:    https://www.github.com/pdimens/PopGenSims.jl/ Documentation: https://biojulia.net/PopGen.jl/

A few things things you can do to get started:

## Import Data using PopGenCore

  * `PopGenCore.read(filename; kwargs...)`
  * `genepop(infile; kwargs...)`  or similar file-specific importer
  * use available `@gulfsharks` or `@nancycats` datasets

## Simulate Samples within Populations

  * `simulate(popdata, n = 100)` to simulate samples using population-specific allele frequencies

## Simulate breeding crosses

  * `cross(popdata, parent1, parent2, ...)` to cross two parents from the same PopData
  * `cross(popdata => parent1, popdata => parent2, ...) to cross two parents from different PopData (e.g. backcross)

## Simulate siblingship

  * `simulatekin(popdata, fullsib = , halfsib = , unrelated = , ...)` to simulate breeding events generating pairs of individuals of known kinship.
