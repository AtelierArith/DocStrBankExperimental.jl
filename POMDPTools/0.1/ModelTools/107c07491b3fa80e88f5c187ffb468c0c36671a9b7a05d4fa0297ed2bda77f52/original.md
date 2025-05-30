```
SparseTabularMDP
```

An MDP object where states and actions are integers and the transition is represented by a list of sparse matrices. This data structure can be useful to exploit in vectorized algorithm (e.g. see SparseValueIterationSolver). The recommended way to access the transition and reward matrices is through the provided accessor functions: `transition_matrix` and `reward_vector`.

# Fields

  * `T::Vector{SparseMatrixCSC{Float64, Int64}}` The transition model is represented as a vector of sparse matrices (one for each action). `T[a][s, sp]` the probability of transition from `s` to `sp` taking action `a`.
  * `R::Array{Float64, 2}` The reward is represented as a matrix where the rows are states and the columns actions: `R[s, a]` is the reward of taking action `a` in sate `s`.
  * `initial_probs::SparseVector{Float64, Int64}` Specifies the initial state distribution
  * `terminal_states::Set{Int64}` Stores the terminal states
  * `discount::Float64` The discount factor

# Constructors

  * `SparseTabularMDP(mdp::MDP)` : One can provide the matrices to the default constructor or one can construct a `SparseTabularMDP` from any discrete state MDP defined using the explicit interface.

Note that constructing the transition and reward matrices requires to iterate over all the states and can take a while. To learn more information about how to define an MDP with the explicit interface please visit https://juliapomdp.github.io/POMDPs.jl/latest/explicit/ .

  * `SparseTabularMDP(smdp::SparseTabularMDP; transition, reward, discount)` : This constructor returns a new sparse MDP that is a copy of the original smdp except for the field specified by the keyword arguments.
