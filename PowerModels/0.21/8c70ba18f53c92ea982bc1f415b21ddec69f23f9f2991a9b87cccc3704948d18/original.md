given a powermodels data dict produces a new data dict that conforms to the following basic network model requirements.

  * no dclines
  * no switches
  * no inactive components
  * all components are numbered from 1-to-n
  * the network forms a single connected component
  * there exactly one phase angle reference bus
  * generation cost functions are quadratic
  * all branches have explicit thermal limits
  * phase shift on all transformers is set to 0.0
  * bus shunts have 0.0 conductance values

users requiring any of the features listed above for their analysis should use the non-basic PowerModels routines.
