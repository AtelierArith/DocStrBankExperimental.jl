```
AlphaVectorPolicy(pomdp::POMDP, alphas, action_map)
```

Construct a policy from alpha vectors.

# Arguments

  * `alphas`: an |S| x (number of alpha vecs) matrix or a vector of alpha vectors.
  * `action_map`: a vector of the actions correponding to each alpha vector

    AlphaVectorPolicy{P<:POMDP, A}

Represents a policy with a set of alpha vectors.

Use `action` to get the best action for a belief, and `alphavectors` and `alphapairs` to 

# Fields

  * `pomdp::P` the POMDP problem
  * `n_states::Int` the number of states in the POMDP
  * `alphas::Vector{Vector{Float64}}` the list of alpha vectors
  * `action_map::Vector{A}` a list of action corresponding to the alpha vectors
