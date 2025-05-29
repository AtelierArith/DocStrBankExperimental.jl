```
mean_time_to_absorption(x)
```

# Definitions

The expected time to absorption is the expected number of steps that the process will take while in the transient super class given that the process started in state $i$.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

A 1D array where element $i$ is the total number of revisits to transient state $i$ before leaving the transient super class.

# Notes

It is advised to have `x` in canonical form already. This is to avoid confusion of what states make up each element of the array ouput.

# Examples

See the following where we have a chain with 2 transient states (states 3 and 4) that go between eachother. One of those states will enter a pre-absorbing state (state 2). And then the pre-absorbing state will enter the absorbing state (state 1) on the next step.

So state 2 should spend no more steps in the transient states and hence should have a time to absorption of 0. State 4 should have 1 more step than state 3 since state 4 must enter state 3 to exit the transient states.

```jldoctest mean_time_to_absorption
using DiscreteMarkovChains
T = [
    1.0 0.0 0.0 0.0;
    1.0 0.0 0.0 0.0;
    0.0 0.2 0.0 0.8;
    0.0 0.0 1.0 0.0;
]
X = DiscreteMarkovChain(T)

mean_time_to_absorption(X)

# output

3-element Array{Float64,1}:
  0.0
  9.000000000000002
 10.000000000000002
```
