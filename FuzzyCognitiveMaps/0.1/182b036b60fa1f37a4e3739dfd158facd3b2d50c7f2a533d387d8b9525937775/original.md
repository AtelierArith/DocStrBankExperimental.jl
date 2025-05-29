```
    create_fcm(;
csv_file::Union{String, Nothing}=nothing,
concepts::Vector{String}=String[],
weights::Matrix{Float64}=Matrix{Float64}(undef, 0, 0),
activation::Function=sigmoid,
initial_state::Union{Vector{Float64}, Nothing}=nothing,
track_history::Bool=false,
external_concepts::Union{Vector{Bool}, Nothing}=nothing)
```

Create a Fuzzy Cognitive Map (FCM) from a CSV file.

# Arguments

  * `csv_file::Union{String, Nothing}`: Path to the CSV file containing the FCM data.
  * `concepts::Vector{String}`: Names of the concepts in the FCM.
  * `weights::Matrix{Float64}`: Weights of the connections between the concepts.
  * `activation::Function`: Activation function for the FCM.
  * `initial_state::Union{Vector{Float64}, Nothing}`: Initial state of the concepts.
  * `track_history::Bool`: Whether to track the state of the FCM at each iteration.
  * `external_concepts::Union{Vector{Bool}, Nothing}`: Whether the concepts are external.
