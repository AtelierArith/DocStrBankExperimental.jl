A structure to represent a game with objectives and constraints parameterized by a vector θ ∈ Rⁿ.

We will assume that the players' primal variables are stacked into a BlockVector x with the i-th block corresponding to the i-th player's decision variable. Similarly, we will assume that the parameter θ has a block structure so that the i-th player's problem depends only upon the i-th block of θ.
