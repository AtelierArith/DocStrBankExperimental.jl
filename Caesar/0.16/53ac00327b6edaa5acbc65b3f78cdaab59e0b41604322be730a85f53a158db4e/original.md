Helper function to generate and calculate the aggregate cost indicative of the discrepancy between  the deconvolution prediction and prescribed measurement of mutliple `Pose2AprilTag4Corners` factors in the factor graph.

The idea is that a bad calibration will give some kind of SLAM result, and if there is enough information then the SLAM result can be used to bootstrap better and better calibration estimates of the camera that was used to capture the AprilTag sightings.  This function is meant to help do that secondary parameter  search inside a factor graph objection, after a regular solution has been found.

Notes

  * `pred, _ = approxDeconv(dfg, fct)`
  * `fct.preimage[1](pred[:,idx], [f_width, f_height, c_width, c_height, taglength])`

      * `fct.preimage[1]` is a function to find the preimage.
  * `obj = (fc_wh) -> fct.preimage[1](pred[:,idx], fc_wh)`

      * `fc_wh = [f_width, f_height, c_width, c_height, 0.172]`
  * `obj2 = (fcwh) -> obj([fcwh[1]; fcwh[1]; fcwh[2]; c_height; taglength])`
  * `result = Optim.optimize(obj, fct.preimage[2], BFGS(), Optim.options(x_tol=1e-8))`

      * A stored starting estimate for optimization `fct.preimage[2]`
