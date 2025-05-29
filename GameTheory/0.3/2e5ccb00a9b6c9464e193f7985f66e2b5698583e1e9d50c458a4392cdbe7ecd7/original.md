```
random_game([rng=GLOBAL_RNG], [S=Float64], nums_actions)
```

Return a random N-player NormalFormGame instance where the payoffs are drawn independently from the uniform distribution on the set as determined by `S`. `S` is a range (such as `0:9`) or a subtype of `Integer` or `AbstractFloat`; in the latter case, the set is [0, 1) for floats and `typemin(S):typemax(S)` for integers.

# Arguments

  * `rng::AbstractRNG=GLOBAL_RNG`: Random number generator used.
  * `S::Union{Type,AbstractRange}`: Set of values from which payoffs are drawn.
  * `nums_actions::NTuple{N,Int}`: Tuple of the numbers of actions, one for each player.

# Returns

  * `::NormalFormGame`: The generated random N-player NormalFormGame.

# Examples

```julia
julia> using GameTheory, Random

julia> rng = MersenneTwister(12345);

julia> g = random_game(rng, (4, 3));

julia> println(g)
4×3 NormalFormGame{2, Float64}:
 [0.562714, 0.586598]  [0.381128, 0.0501668]  [0.922317, 0.61179]
 [0.849939, 0.620099]  [0.365801, 0.215712]   [0.0404417, 0.569955]
 [0.371605, 0.965631]  [0.835014, 0.364706]   [0.573382, 0.923602]
 [0.283365, 0.754047]  [0.260024, 0.696476]   [0.981364, 0.0311643]

julia> g = random_game(rng, 0:9, (4, 3));

julia> println(g)
4×3 NormalFormGame{2, Int64}:
 [1, 5]  [1, 2]  [6, 2]
 [2, 5]  [0, 2]  [1, 0]
 [0, 5]  [3, 9]  [1, 1]
 [9, 5]  [2, 9]  [0, 6]
```
