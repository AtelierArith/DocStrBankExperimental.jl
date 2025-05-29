```
NFQ{A<:AbstractApproximator, F, R} <: AbstractLearner
NFQ(action_space::AbstractVector, approximator::A, num_iterations::Integer epochs::Integer, loss_function::F, rng::R, γ::Float32) where {A, F, R}
```

Neural Fitted Q-iteration as implemented in [1]

# Keyword arguments

  * `action_space::AbstractVector` Action space of the environment (necessary in the optimise! step)
  * `approximator::A` Q-function approximator (typically a neural network)
  * `num_iterations::Integer` number of value iteration iterations in FQI loop (i.e. the outer loop)
  * `epochs::Integer` number of epochs to train neural network per iteration
  * `loss_function::F` loss function of the NN
  * `rng::R` random number generator
  * `γ::Float32` discount rate

# References

[1] Riedmiller, M. (2005). Neural Fitted Q Iteration – First Experiences with a Data Efficient Neural Reinforcement Learning Method. In: Gama, J., Camacho, R., Brazdil, P.B., Jorge, A.M., Torgo, L. (eds) Machine Learning: ECML 2005. ECML 2005. Lecture Notes in Computer Science(), vol 3720. Springer, Berlin, Heidelberg. https://doi.org/10.1007/11564096_32
