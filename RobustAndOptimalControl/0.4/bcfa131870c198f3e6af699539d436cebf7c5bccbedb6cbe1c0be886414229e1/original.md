```
LQGProblem(P::ExtendedStateSpace)
```

If only an `ExtendedStateSpace` system is provided, e.g. from `hinfpartition`, the system `P` is assumed to correspond to the H₂ optimal control problem with

```
C1'C1    = Q1
D12'D12  = Q2
SQ       = C1'D12 # Cross term

B1*B1'   = R1
D21*D21' = R2
SR       = B1*D21' # Cross term
```

and an `LQGProblem` with the above covariance matrices is returned. The system description in the returned LQGProblem will have `B1 = C1 = I`. See Ch. 14 in Robust and optimal control for reference. 

# Example:

All the following ways of obtaining the H2 optimal controller are (almost) equivalent

```julia
using Test
G = ss(tf(1, [10, 1]))
WS = tf(1, [1, 1e-6]) 
WU = makeweight(1e-2, 0.1, 100) 
Gd = hinfpartition(G, WS, WU, [])

K, Gcl = h2synthesize(Gd)              # First option, using H2 formulas
K2, Gcl2 = h2synthesize(Gd, 1000)      # Second option, using H∞ formulas with large γ

lqg = LQGProblem(Gd)                   # Third option, convert to an LQGProblem and obtain controller
K3 = -observer_controller(lqg)

@test h2norm(lft(Gd, K )) ≈ 3.0568 atol=1e-3
@test h2norm(lft(Gd, K2)) ≈ 3.0568 atol=1e-3
@test h2norm(lft(Gd, K3)) ≈ 3.0568 atol=1e-3
```
