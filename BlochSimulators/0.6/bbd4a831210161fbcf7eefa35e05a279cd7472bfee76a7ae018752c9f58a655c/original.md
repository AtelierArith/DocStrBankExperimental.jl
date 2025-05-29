```
BlochSimulator{T}
```

The abstract type of which all sequence simulators will be a subtype. The parameter `T` should be a number type (e.g. `Float64`, `Float32`) and the tissueparameters that are used as input to the simulator should have the same number type. By convention, a BlochSimulator will be used to simulate magnetization at echo times only without taking into account spatial encoding gradients (i.e. readout or phase encoding gradients). To simulate the magnetization at other readout times, including phase from spatial encoding gradients, an `AbstractTrajectory` will be needed as well.

To make a simulator for a particular pulse sequence:

1. Make a struct that's a subtype of either `IsochromatSimulator` or `EPGSimulator`.  The struct will hold parameters that are necessary for performing the simulations.
2. Add a method to `simulate_magnetization!` that implements the pulse sequence. For both performance and GPU compatibility,  make sure that `simulate_magnetization!` does not do any heap allocations. Examples for `pSSFP` and `FISP`  sequences are found in `src/sequences`.
3. Add methods to `output_eltype` and `output_size` that are used to allocate an output array within the simulate function.
4. [Optional] Add a method to show for nicer printing of the sequence in the REPL
5. [Optional] Add a method to getindex to easily reduce the length of the sequence
6. [Optional] Add a constructor for the struct that takes in data from Matlab or  something else and assembles the struct

**IMPORTANT**

The `simulate_magnetization!` functions (which dispatch on the provided sequence) are assumed to be type-stable and non-allocating Should be possible to achieve when using functions from `operators/epg.jl``and`operators/isochromat.jl` and a properly parametrized sequence struct.
