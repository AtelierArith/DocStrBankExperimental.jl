```
covariance_game([rng=GLOBAL_RNG], nums_actions, rho)
```

Return a random N-player NormalFormGame instance with N>=2 where the payoff profiles are drawn independently from the standard multi-normal with the covariance of any pair of payoffs equal to `rho`, as studied in Rinott and Scarsini (2000).

# Arguments

  * `rng::AbstractRNG=GLOBAL_RNG`: Random number generator used.
  * `nums_actions::NTuple{N,Int}`: Tuple of the numbers of actions, one for each player.
  * `rho::Real`: Covariance of a pair of payoff values. Must be in [-1/(N-1), 1], where N is the number of players.

# Returns

  * `::NormalFormGame`: The generated random N-player NormalFormGame.

# Examples

```julia
julia> using GameTheory, Random

julia> rng = MersenneTwister(12345);

julia> g = covariance_game(rng, (4, 3), -0.7);

julia> println(g)
4×3 NormalFormGame{2, Float64}:
 [1.17236, -0.211696]   [1.46647, -1.13947]    [0.378353, 0.603951]
 [0.415565, 0.0779055]  [0.606808, 1.00812]    [1.12871, -1.03399]
 [0.685759, -0.278449]  [-0.588508, 0.464548]  [-0.970332, -0.0319236]
 [-1.47708, 1.12447]    [1.92585, -2.27959]    [-2.1476, 1.53569]
```

# References

  * Y. Rinott and M. Scarsini, "On the Number of Pure Strategy Nash Equilibria in Random Games," Games and Economic Behavior (2000), 274-293.
