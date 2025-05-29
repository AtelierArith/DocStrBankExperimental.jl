```
probNFE(neuralFieldEquation)
```

Pre-process the neural field equation in order to be computed by `solveNFE`

`probNFE` receives as input the parameters and functions wrapped in the structures `Input1D` and `Input2D`.

# Examples

```julia-repl
julia> # 2D example
julia> I(x,y,t) = 1                      # External input
julia> K(x,y)   = exp(-x^2+y^2)          # Connectivity function
julia> S(V)     = convert(Float64,V>0.0) # Firing rate. Heavyside function H(V)

julia> α  = 1.0  # Constant decay
julia> v  = 20.0 # Finite axonal speed
julia> V0 = 0.0  # Initial condition
julia> L  = 100  # Domain length
julia> N  = 512  # Number of nodes to discretise space
julia> T  = 20.0 # Time span
julia> n  = 200  # Number of nodes to discretise time

julia> nf   = Input2D(α,v,V0,L,N,T,n,I,K,S);
julia> prob = probNFE(nf)
├─ Domain:       Ω × [0,T] = [-50.0,49.8046875]^2 × [0,20.0]
├─ Spatial step: dx   = 0.1953125
├─ Time step:    dt   = 0.1
├─ Velocity:     v    = 20.0
├─ Delay rings:  umax = 36
```

For 1D domains the procedure is the same but the inputs are wrapped using `Input1D`.
