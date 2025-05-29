```
DiscreteExplicitPOMDP(S,A,O,T,Z,R,γ,[b₀],[terminals=Set()])
```

Create a POMDP defined by the tuple (S,A,O,T,Z,R,γ).

# Arguments

## Required

  * `S`,`A`,`O`: State, action, and observation spaces (typically `Vector`s)
  * `T::Function`: Transition probability distribution function; $T(s,a,s')$ is the probability of transitioning to state $s'$ from state $s$ after taking action $a$.
  * `Z::Function`: Observation probability distribution function; $O(a, s', o)$ is the probability of receiving observation $o$ when state $s'$ is reached after action $a$.
  * `R::Function`: Reward function; $R(s,a)$ is the reward for taking action $a$ in state $s$.
  * `γ::Float64`: Discount factor.

## Optional

  * `b₀=Uniform(S)`: Initial belief/state distribution (See `POMDPModelTools.Deterministic` and `POMDPModelTools.SparseCat` for other options).

## Keyword

  * `terminals=Set()`: Set of terminal states. Once a terminal state is reached, no more actions can be taken or reward received.
