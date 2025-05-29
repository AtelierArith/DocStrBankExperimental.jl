The structure for storing a projection-based representation of differential ideal (see Section 2.3 https://arxiv.org/abs/2111.00991). Contains the following fields:

  * `y_names` - the names of the variables with finite order in the profile (typically, outputs)
  * `u_names` - the names of the variables with infinite order in the profile (typically, inputs)
  * `param_names` - the names of the parameters
  * `profile` - the profile of the PB-representation (see Definition 2.13) as a dict from `y_names` with finite orders to the orders
  * `projections` - the corresponding projections (see Definition 2.15) as a dict from `y_names` to the projections
