```
setup_growth(Ωm, ΩΛ[, a1=1e-2])
```

Return the solutions of coupled differential equations given in `growth!`, with the initial condition such that $δ(a) = a$ at `a = a1`. The default value is `a1 = 1e-2`.

# Arguments

  * `Ωm::Real`: present-day total matter density parameter.
  * `ΩΛ::Real`: present-day dark energy density parameter (for cosmological constant).

# Optional arguments

  * `a1::Real=1e-2`: initial scale factor, at which the initial condition is set as δ(a1) = a1.

# Examples

```julia-repl
julia> Ωm, ΩΛ = 0.3, 0.7
(0.3, 0.7)

julia> sol = MatterPower.setup_growth(Ωm, ΩΛ)
retcode: Success
Interpolation: specialized 4th order "free" interpolation
t: 14-element Array{Float64,1}:
 0.01
 0.022952118470240847
 0.03152976635130906
 0.04919933323749941
 ⋮
 0.7292247303730331
 0.994509796947469
 1.0
u: 14-element Array{Array{Float64,1},1}:
 [0.01, -0.05477231965144438]
 [0.022953661875878814, -0.08298398087457971]
 [0.0315315317884963, -0.09726149943169236]
 [0.049200231832575124, -0.12149028570497]
 ⋮
 [0.6428440417117532, -0.39916939875846624]
 [0.7768316486186253, -0.3997506971222691]
 [0.7790350080966789, -0.3994861471523371]

julia> redshift = 1.2
1.2

julia> a = 1/(1+redshift)
0.45454545454545453

julia> δ = sol(a)[1]
0.43811688788577136

julia> θ = sol(a)[2]
-0.3526347043144974
```
