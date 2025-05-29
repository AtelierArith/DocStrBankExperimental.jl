Fill `X` with sample paths of the Markov chain `mc` as columns. The resulting matrix has the indices of the state values of `mc` as elements.

### Arguments

  * `X::Matrix{Int}` : Preallocated matrix to be filled with indices

of the sample paths of the Markov chain `mc`.

  * `mc::MarkovChain` : MarkovChain instance.
  * `;init=rand(1:n_states(mc))` : Can be one of the following

      * blank: random initial condition for each chain
      * scalar: same initial condition for each chain
      * vector: cycle through the elements, applying each as an initial condition until all columns have an initial condition (allows for more columns than initial conditions)
