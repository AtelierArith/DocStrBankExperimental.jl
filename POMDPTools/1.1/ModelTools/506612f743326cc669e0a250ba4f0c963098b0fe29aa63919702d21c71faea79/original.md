```
SparseTabularPOMDP
```

A POMDP object where states and actions are integers and the transition and observation distributions are represented by lists of sparse matrices. This data structure can be useful to exploit in vectorized algorithms to gain performance (e.g. see SparseValueIterationSolver). The recommended way to access the transition, reward, and observation matrices is through the provided accessor functions: `transition_matrix`, `reward_vector`, `observation_matrix`.

# Fields

  * `T::Vector{SparseMatrixCSC{Float64, Int64}}` The transition model is represented as a vector of sparse matrices (one for each action). `T[a][s, sp]` the probability of transition from `s` to `sp` taking action `a`.
  * `R::Array{Float64, 2}` The reward is represented as a matrix where the rows are states and the columns actions: `R[s, a]` is the reward of taking action `a` in sate `s`.
  * `O::Vector{SparseMatrixCSC{Float64, Int64}}` The observation model is represented as a vector of sparse matrices (one for each action). `O[a][sp, o]` is the probability of observing `o` from state `sp` after having taken action `a`.
  * `initial_probs::SparseVector{Float64, Int64}` Specifies the initial state distribution
  * `terminal_states::Set{Int64}` Stores the terminal states
  * `discount::Float64` The discount factor

# Constructors

  * `SparseTabularPOMDP(pomdp::POMDP)` : One can provide the matrices to the default constructor or one can construct a `SparseTabularPOMDP` from any discrete state MDP defined using the explicit interface.

Note that constructing the transition and reward matrices requires to iterate over all the states and can take a while. To learn more information about how to define an MDP with the explicit interface please visit https://juliapomdp.github.io/POMDPs.jl/latest/explicit/ .

  * `SparseTabularPOMDP(spomdp::SparseTabularMDP; transition, reward, observation, discount)` : This constructor returns a new sparse POMDP that is a copy of the original smdp except for the field specified by the keyword arguments.
