```
OrthogonalIntervalMarkovDecisionProcess{
    P <: OrthogonalIntervalProbabilities,
    VT <: AbstractVector{Int32},
    VI <: Union{AllStates, AbstractVector}
}
```

A type representing (stationary) Orthogonal Interval Markov Decision Processes (OIMDP), which are IMDPs where the transition  probabilities for each state can be represented as the product of the transition probabilities of individual processes.

Formally, let $(S, S_0, A, \Gamma)$ be an orthogonal interval Markov decision process [1], where

  * $S = S_1 \times \cdots \times S_n$ is the set of joint states with $S_i$ the set of states for the `i`-th marginal,
  * $S_0 \subseteq S$ is the set of initial states,
  * $A$ is the set of actions, and
  * $\Gamma = \{\Gamma_{s,a}\}_{s \in S, a \in A}$ is a set of interval ambiguity sets on the transition probabilities,  for each source-action pair, with $\Gamma_{s,a} = \bigotimes_{i=1}^n \Gamma_{s,a}^i$ and $\Gamma_{s,a}^i$ is a marginal interval ambiguity sets on the $i$-th marginal.

Then the `OrthogonalIntervalMarkovDecisionProcess` type is defined as follows: indices `1:num_states` are the states in $S$ and  `transition_prob` represents $\Gamma$. Actions are implicitly defined by `stateptr` (e.g. if `source_dims` in `transition_prob` is `(2, 3, 2)`, and `stateptr[3] == 4` and `stateptr[4] == 7` then the actions available to state `CartesianIndex(1, 2, 1)` are `[1, 2, 3]`), and `initial_states` is the set of initial states $S_0$. If no initial states are specified, then the initial states are assumed to be all states in $S$ represented by `AllStates`. See [OrthogonalIntervalProbabilities](@ref) and [Theory](@ref) for more information on the structure of the transition probability ambiguity sets.

### Fields

  * `transition_prob::P`: interval on transition probabilities where columns represent source/action pairs and rows represent target states along each marginal.
  * `stateptr::VT`: pointer to the start of each source state in `transition_prob` (i.e. `transition_prob[l][:, stateptr[j]:stateptr[j + 1] - 1]` is the transition   probability matrix for source state `j` for each axis `l`) in the style of colptr for sparse matrices in CSC format.
  * `initial_states::VI`: initial states.
  * `num_states::Int32`: number of states.

### Examples

Assume that `prob1`, `prob2`, and `prob3` are `IntervalProbabilities` for the first, second, and third axis, respectively, defined as the example  in [OrthogonalIntervalProbabilities](@ref). Then the following code constructs an `OrthogonalIntervalMarkovDecisionProcess` with three axes of three states each. The number of actions per state is one, i.e. the model is a Markov chain. Therefore, the `stateptr` is a unit range `1:num_states + 1` and we can call the convenience constructor `OrthogonalIntervalMarkovChain` instead.

```jldoctest
prob = OrthogonalIntervalProbabilities((prob1, prob2, prob3), (Int32(3), Int32(3), Int32(3)))
mc = OrthogonalIntervalMarkovChain(prob)
```

[1] Mathiesen, F. B., Haesaert, S., & Laurenti, L. (2024). Scalable control synthesis for stochastic systems via structural IMDP abstractions. arXiv preprint arXiv:2411.11803.
