`measure_rvs_from_ccf(vels, ccf, [ccf_var]; alg )` At each time, return the estimated radial velocities based on the CCFs using the specified algorithm. Inputs:

  * `vels`: Array of velocites where CCF was evaluated.
  * `ccf`:  Array of values of CCF

Optional Arguements:

  * `alg`: Functor specifying how to measure the RV and its uncertainty from the CCF.  Options include:

MeasureRvFromCCFGaussian (default), MeasureRvFromCCFQuadratic, MeasureRvFromCCFCentroid, and MeasureRvFromMinCCF.
