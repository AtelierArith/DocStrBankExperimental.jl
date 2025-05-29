Linearized 'DC' power flow model with polar voltage variables.

Similar to the DCPPowerModel with the following changes:

  * It uses branch susceptance values `br_b = -1 / br_x` for determining the network phase angles.
  * Transformer parameters such as tap ratios and phase shifts are considered.

The results should be equal to the results of matpower calculations.
