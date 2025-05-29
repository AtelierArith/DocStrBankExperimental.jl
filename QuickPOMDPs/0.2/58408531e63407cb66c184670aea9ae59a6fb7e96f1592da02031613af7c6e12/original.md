```
DiscreteExplicitMDP(S,A,T,R,γ,[p₀],[terminals=Set()])
```

Create an MDP defined by the tuple (S,A,T,R,γ).

# Arguments

## Required

  * `S`,`A`: State and action spaces (typically `Vector`s)
  * `T::Function`: Transition probability distribution function; $T(s,a,s')$ is the probability of transitioning to state $s'$ from state $s$ after taking action $a$.
  * `R::Function`: Reward function; $R(s,a)$ is the reward for taking action $a$ in state $s$.
  * `γ::Float64`: Discount factor.

## Optional

  * `p₀=Uniform(S)`: Initial state distribution (See `POMDPModelTools.Deterministic` and `POMDPModelTools.SparseCat` for other options).

## Keyword

  * `terminals=Set()`: Set of terminal states. Once a terminal state is reached, no more actions can be taken or reward received.
