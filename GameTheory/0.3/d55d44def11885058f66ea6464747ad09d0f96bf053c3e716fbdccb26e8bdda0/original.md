```
hc_solve(g; ntofind=Inf, options...)
```

Compute all isolated mixed-action Nash equilibria of an N-player normal form game.

This function solves a system of polynomial equations arising from the nonlinear complementarity problem representation of Nash eqiulibrium, by using `HomotopyContinuation.jl`.

# Arguments

  * `g::NormalFormGame`: N-player NormalFormGame instance.
  * `ntofind=Inf`: Number of Nash equilibria to find.
  * `options...`: Optional arguments to pass to `HomotopyContinuation.solve`. For example, the option `seed::UInt32` can set the random seed used during the computations. See the [documentation](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/solve/) for `HomotopyContinuation.solve` for details.

# Returns

  * `::Vector{NTuple{N,Vector{Float64}}}`: Vector of mixed-action Nash equilibria.

# Examples

Consider the 3-player 2-action game with 9 Nash equilibria in McKelvey and McLennan (1996) "Computation of Equilibria in Finite Games":

```julia
julia> Base.active_repl.options.iocontext[:compact] = true;  # Reduce digits to display

julia> g = NormalFormGame((2, 2, 2));

julia> g[1, 1, 1] = [9, 8, 12];

julia> g[2, 2, 1] = [9, 8, 2];

julia> g[1, 2, 2] = [3, 4, 6];

julia> g[2, 1, 2] = [3, 4, 4];

julia> println(g)
2×2×2 NormalFormGame{3, Float64}:
[:, :, 1] =
 [9.0, 8.0, 12.0]  [0.0, 0.0, 0.0]
 [0.0, 0.0, 0.0]   [9.0, 8.0, 2.0]

[:, :, 2] =
 [0.0, 0.0, 0.0]  [3.0, 4.0, 6.0]
 [3.0, 4.0, 4.0]  [0.0, 0.0, 0.0]

julia> NEs = hc_solve(g, show_progress=false)
9-element Vector{Tuple{Vector{Float64}, Vector{Float64}, Vector{Float64}}}:
 ([0.0, 1.0], [0.333333, 0.666667], [0.333333, 0.666667])
 ([1.0, 0.0], [0.0, 1.0], [0.0, 1.0])
 ([0.25, 0.75], [0.5, 0.5], [0.333333, 0.666667])
 ([0.5, 0.5], [0.5, 0.5], [1.0, -7.34684e-40])
 ([0.0, 1.0], [1.0, 0.0], [-2.93874e-39, 1.0])
 ([0.0, 1.0], [0.0, 1.0], [1.0, 0.0])
 ([0.5, 0.5], [0.333333, 0.666667], [0.25, 0.75])
 ([1.0, 4.48416e-44], [1.0, -7.17465e-43], [1.0, -4.48416e-44])
 ([0.25, 0.75], [1.0, 0.0], [0.25, 0.75])

julia> all([is_nash(g, NE) for NE in NEs])
true
```
