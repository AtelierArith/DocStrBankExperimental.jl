`Input1D` is a structure to wrap the inputs to pass to `probNFE` function. The arguments are in the following order:

# Input1D arguments

  * `α  :: AbstractFloat`
  * `v  :: AbstractFloat`
  * `V0 :: fV0`: Can be a number or a function
  * `L  :: Number`
  * `N  :: Integer`
  * `T  :: AbstractFloat`
  * `n  :: Integer`
  * `I  :: fI`: External input function
  * `K  :: fK`: Connectivity function
  * `S  :: fS`: Firing rate function

Declaration of `I`, `K` and `S` functions:

  * The function I must have the arguments: `I(x,t)`
  * The function K must have the arguments: `K(x)`
  * The function S must have the arguments: `S(V)`
