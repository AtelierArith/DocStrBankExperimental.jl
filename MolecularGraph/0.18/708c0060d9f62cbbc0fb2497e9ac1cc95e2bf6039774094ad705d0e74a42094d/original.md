```
simulate_massspec(peaks::Vector{Tuple{Float64,Float64}};
    resolution=10000, rate=0.01) -> Matrix{Float64}
simulate_massspec(mol::MolGraph;
    threshold=0.001, resolution=10000, rate=0.01) -> Matrix{Float64}
```

Return a matrix of simulate mass spectrum (dim 1: datapoints, dim 2: mass and intensity).

Note that the peaks are just calculated from the isotopic composition of atoms (not intended for simulation of fragmentation).

# Usage (with Plot.jl)

```julia
using MolecularGraph
using Plots
gr()
Plots.GRBackend()

mol = smilestomol("CCO")
data = simulatemassspec(mol)
plot(
    data[:, 1], data[:, 2],
    leg=false, xlabel = "Mass", ylabel = "Intensity"
)
```
