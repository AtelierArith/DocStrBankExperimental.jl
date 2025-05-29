```
expect(psi::MPS, op::AbstractString...; kwargs...)
expect(psi::MPS, op::Matrix{<:Number}...; kwargs...)
expect(psi::MPS, ops; kwargs...)
```

Given an MPS `psi` and a single operator name, returns a vector of the expected value of the operator on each site of the MPS.

If multiple operator names are provided, returns a tuple of expectation value vectors.

If a container of operator names is provided, returns the same type of container with names replaced by vectors of expectation values.

# Optional Keyword Arguments

  * `sites = 1:length(psi)`: compute expected values only for sites in the given range

# Examples

```julia
N = 10

s = siteinds("S=1/2", N)
psi = randomMPS(s; linkdims=8)
Z = expect(psi, "Sz") # compute for all sites
Z = expect(psi, "Sz"; sites=2:4) # compute for sites 2,3,4
Z3 = expect(psi, "Sz"; sites=3)  # compute for site 3 only (output will be a scalar)
XZ = expect(psi, ["Sx", "Sz"]) # compute Sx and Sz for all sites
Z = expect(psi, [1/2 0; 0 -1/2]) # same as expect(psi,"Sz")

s = siteinds("Electron", N)
psi = randomMPS(s; linkdims=8)
dens = expect(psi, "Ntot")
updens, dndens = expect(psi, "Nup", "Ndn") # pass more than one operator
```
