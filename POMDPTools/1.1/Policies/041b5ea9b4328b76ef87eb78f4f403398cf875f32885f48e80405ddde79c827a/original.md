```
PlaybackPolicy{A<:AbstractArray, P<:Policy, V<:AbstractArray{<:Real}}
```

a policy that applies a fixed sequence of actions until they are all used and then falls back onto a backup policy until the end of the episode.

Constructor:

```
`PlaybackPolicy(actions::AbstractArray, backup_policy::Policy; logpdfs::AbstractArray{Float64, 1} = Float64[])`
```

# Fields

  * `actions::Vector{A}` a vector of actions to play back
  * `backup_policy::Policy` the policy to use when all prescribed actions have been taken but the episode continues
  * `logpdfs::Vector{Float64}` the log probability (density) of actions
  * `i::Int64` the current action index
