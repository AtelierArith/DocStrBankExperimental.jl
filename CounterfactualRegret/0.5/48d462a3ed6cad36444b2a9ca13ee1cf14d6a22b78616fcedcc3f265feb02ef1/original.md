```
ESCFRSolver(game::Game; method::Symbol=:vanilla, alpha::Float64 = 1.0, beta::Float64 = 1.0, gamma::Float64 = 1.0, d::Int)
```

Instantiate external sampling CFR solver with some `game`.

Samples a single actions from all players for single tree traversal. Time to complete a traversal is O(|𝒜ᵢ|ᵈ), where d is the depth of the game and |𝒜ᵢ| is the size of the action space for the acting player.
