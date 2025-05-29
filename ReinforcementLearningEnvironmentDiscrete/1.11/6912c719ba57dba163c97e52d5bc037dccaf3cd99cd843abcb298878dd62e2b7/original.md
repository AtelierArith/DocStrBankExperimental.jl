```
mutable struct MDP 
    ns::Int64
    na::Int64
    state::Int64
    trans_probs::Array{AbstractArray, 2}
    reward::Array{Float64, 2}
    initialstates::Array{Int64, 1}
    isterminal::Array{Int64, 1}
```

A Markov Decision Process with `ns` states, `na` actions, current `state`, `na`x`ns` - array of transition probabilites `trans_props` which consists for every (action, state) pair of a (potentially sparse) array that sums to 1 (see [`getprobvecrandom`](@ref), [`getprobvecuniform`](@ref), [`getprobvecdeterministic`](@ref) for helpers to constract the transition probabilities) `na`x`ns` - array of `reward`, array of initial states `initialstates`, and `ns` - array of 0/1 indicating if a state is terminal.
