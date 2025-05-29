Fill `X` with sample paths of the Markov chain `mc` as columns. The resulting matrix has the state values of `mc` as elements.

### Arguments

  * `X::Matrix` : Preallocated matrix to be filled with sample paths

of the Markov chain `mc`. The element types in `X` should be the same as the type of the state values of `mc`

  * `mc::MarkovChain` : MarkovChain instance.
  * `;init=rand(1:n_states(mc))` : Can be one of the following

      * blank: random initial condition for each chain
      * scalar: same initial condition for each chain
      * vector: cycle through the elements, applying each as an initial condition until all columns have an initial condition (allows for more columns than initial conditions)
