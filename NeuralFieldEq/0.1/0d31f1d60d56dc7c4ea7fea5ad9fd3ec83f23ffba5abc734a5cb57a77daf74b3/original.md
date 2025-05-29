```
solveNFE(problem,saveat)
```

# Arguments:

  * `problem :: ProbOutput1D`: Output of probNFE using Input1D structure
  * `problem :: ProbOutput2D`: Output of probNFE using Input2D structure
  * `saveat  :: AbstractVector`: Vector containing the instants where the solution is saved at

Returns a structure containing the solution to the NFE saved at saveat instants. The structure has `x`, `y` and `saveat` as fields to help plotting the solution.

# Examples

```julia-repl
julia> # 2D example
julia> saveat = [5.0,20.0]
julia> sol    = solveNFE(prob,saveat) # Deterministic solution saved at t=5 and t=20
julia> sol(20.0) # Solution at t=20
julia> x = sol.x # Spatial vector in x direction 
julia> y = sol.y # Spatial vector in y direction
julia> using Plots
julia> plot(x,y,sol(20.0),st=:surface,title="Solution at t=20") # Surface plot of sol(20.0)
```

If the neural field is in 1D/2D, the solution is a vector/matrix.

---

```
solveNFE(problem,saveat,ϵ,np,ξ=0.1)
```

Solve stochastic version of an NFE for np trajectories, noise level ϵ and correlation ξ.

# Arguments:

  * `problem :: ProbOutput1D`: Output of probNFE with Input1D
  * `problem :: ProbOutput2D`: Output of probNFE with Input2D
  * `saveat  :: AbstractVector`: Vector containing the instants where the solution is saved at
  * `ϵ       :: Number`: Level of additive noise
  * `np      :: Integer`: Number of simulations
  * `ξ       :: AbstractFloat=0.1`: Spatial correlation parameter

Returns a structure containing the mean solution and the trajectories of the NFE saved at saveat instants.

# Examples

```julia-repl
julia> # Stochastic solution saved at t=5,20, with noise level 0.01 simulated 100 times.
julia> sol_sto = solveNFE(prob,saveat,0.01,100)
julia> sol_sto(20.0,4) # 4th path at t=20
julia> sol_sto(5.0)    # Mean solution at t=20
```
