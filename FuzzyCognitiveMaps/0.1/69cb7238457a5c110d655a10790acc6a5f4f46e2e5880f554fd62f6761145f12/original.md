```
create_fcm(concepts::Vector{String}, weights::Matrix{Float64},
           activation::Function, initial_state::Vector{Float64};
           track_history::Bool=false,
           external_concepts::Vector{Bool}=falses(length(concepts)))
```

Create a new Fuzzy Cognitive Map (FCM) with the specified parameters.

# Arguments

  * `concepts::Vector{String}`: Names of the concepts in the FCM
  * `weights::Matrix{Float64}`: Adjacency matrix representing the causal weights between concepts
  * `activation::Function`: Activation function to be applied during state updates
  * `initial_state::Vector{Float64}`: Initial activation values for each concept
  * `track_history::Bool=false`: Whether to track state history during updates
  * `external_concepts::Vector{Bool}`: Indicates which concepts are external (fixed during updates)

# Returns

  * `FuzzyCognitiveMap`: A new FCM instance initialized with the given parameters
