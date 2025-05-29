```
`measure_rv_from_ccf(vels, ccf, [ccf_var]; alg )`
```

Return estimated RV based on the CCF using specified algorithm object. Inputs:

  * `vels`: Array of velocites where CCF was evaluated.
  * `ccf`:  Array of values of CCF

Optional Arguements:

  * `alg`: Functor specifying how to measure the RV and it's uncertainty from the CCF.  Options include:

MeasureRvFromCCFGaussian (default), MeasureRvFromCCFQuadratic, MeasureRvFromCCFCentroid, and MeasureRvFromMinCCF.
