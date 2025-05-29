Solves the PTDF variant of the OPF problem by iteratively adding line flow constraints based on constraint violations.

Currently the DCPPowerModel is used in this solver as that is the only model supporting the PTDF problem specification at this time.

# Keyword Arguments

  * `max_iter`: maximum number of flow iterations to perform.
  * `time_limit`: maximum amount of time (sec) for the algorithm.
  * `full_inverse`: compute the complete admittance matrix inverse, instead of a branch by branch computation.
