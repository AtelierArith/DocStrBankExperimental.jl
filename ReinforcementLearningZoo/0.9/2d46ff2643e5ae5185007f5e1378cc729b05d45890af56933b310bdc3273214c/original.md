```
BasicDQNLearner(;kwargs...)
```

See paper: [Playing Atari with Deep Reinforcement Learning](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf)

This is the very basic implementation of DQN. Compared to the traditional Q learning, the only difference is that, in the optimising step it uses a batch of transitions sampled from an experience buffer instead of current transition. And a neural network is used to estimate the Q-value.  You can start from this implementation to understand how everything is organized and how to write your own customized algorithm.

# Keyword Arguments

  * `approximator`::[`Approximator`](@ref): used to get Q-values of a state.
  * `loss_func=huber_loss`: the loss function to use.
  * `γ::Float32=0.99f0`: discount rate.
