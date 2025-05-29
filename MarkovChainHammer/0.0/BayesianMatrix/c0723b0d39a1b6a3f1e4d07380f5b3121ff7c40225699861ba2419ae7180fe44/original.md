```
GeneratorParameterDistributions(number_of_states::Int; α=1, β=1, αs=ones(number_of_states - 1))
```

Construct a GeneratorParameterDistributions object with Gamma(α, 1/β) prior distributions for the rates and Dirichlet(αs) prior distributions for the exit probabilities. Each state has the same probability distribution This is useful for construction prior distributions quickly. The underlying assumption for default rates is that the units of time are 1, and thus the rates are all by default 1. Futhermore the mean probability of each state is  1/(number*of*states-1)

The reason why the αs is of length(number*of*states - 1) is because they are exit probabilities, and hence the probability of returning to the same state is 0. The index ordering for the exit probability of state i, is [1:i-1..., i+1:number*of*states...].  For example, if number*of*states = 3, then the index ordering for state 1 is indices = [2, 3], i.e., indices[1] = 2 and indices[2] = 3, meaning, the first index corresponds to exiting through state 2 and the second index corresponds to exiting through state 3. The index ordering for state 2 is indices = [1, 3], i.e., indices[1] = 1 and indices[2] = 3, meaning, the first index corresponds to exiting through state 1 and the second index corresponds to exiting through state 3. The index ordering for state 3 is indices = [1, 2], i.e., indices[1] = 1 and indices[2] = 2, meaning, the first index corresponds to exiting through state 1 and the second index corresponds to exiting through state 2.

# Arguments

  * `number_of_states::Int`: The number of states in the Markov chain.

# Keyword Arguments

  * `α::Number=2`: The shape parameter for the Gamma prior distribution for the rates.
  * `β::Number=2`: The rate parameter for the Gamma prior distribution for the rates.
  * `αs::Vector{Number}=ones(number_of_states - 1)`: The concentration parameters for the Dirichlet prior distribution for the exit probabilities.

# Returns

  * `GeneratorParameterDistributions`: A GeneratorParameterDistributions object with Gamma(α, 1/β) prior distributions for the rates and Dirichlet(αs) prior distributions for the exit probabilities.

# Note on the Gamma prior distribution (from https://en.wikipedia.org/wiki/Gamma_distribution)

The Gamma distribution is a conjugate prior distribution for the exponential family distribution of the rates. The Gamma distribution is parameterized by the shape parameter α and the rate parameter β. The mean of the Gamma distribution is α/β and the variance is α/β^2.

# Note on the Dirichlet prior distribution (from https://en.wikipedia.org/wiki/Dirichlet_distribution)

The Dirichlet prior distribution is a conjugate prior distribution for the multinomial distribution of the exit probabilities. The Dirichlet prior distribution is parameterized by the concentration parameters αs.  The mean of the Dirichlet distribution is E[X⃗] = αs/sum(αs)  The covariance is CoVar[X⃗ ⊗ X⃗] = Diagonal(α̃) - α̃ ⊗ α̃ / (α₀ + 1) where α̃ = αs / α₀  and α₀ = sum(αs). The variance Var(Xᵢ) = α̃ᵢ(1-α̃ᵢ) / (α₀ + 1) where α₀ = sum(αs).
