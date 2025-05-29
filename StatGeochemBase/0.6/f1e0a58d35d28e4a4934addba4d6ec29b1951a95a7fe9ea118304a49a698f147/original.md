```julia
mcmc_surface(xaxis::AbstractRange, yaxis::AbstractRange, llmatrix::AbstractMatrix; 
    nsteps::Int=100000, 
    burnin::Int=10000,
)
```

Explore a precomputed log likelihood surface `llmatrix` with dimensions  `xaxis` (horizontal, columns) and `yaxis` (vertical, rows) using a  Markov chain Monte Carlo approach (the Metropolis algorithm) to calculate posterior distributions for x and y.

### Examples

```julia
julia> xaxis = yaxis = -5:0.01:5
 -5.0:0.01:5.0

julia> llmatrix = [-((x+1)^2/0.5^2 + (y-1)^2/0.5^2) for y in yaxis, x in xaxis];

julia> xdist, ydist, lldist, acceptancedist = mcmc_surface(xaxis,yaxis,llmatrix);

julia> mean(xdist), std(xdist)
 (-0.9888633375860412, 0.41023499283715603)

julia> mean(ydist), std(ydist)
 (1.0110703489524537, 0.4182564675721746)
```
