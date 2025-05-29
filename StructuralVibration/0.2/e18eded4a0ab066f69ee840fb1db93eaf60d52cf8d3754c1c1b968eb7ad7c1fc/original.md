```
modeshape_extraction(freq, H, fn, ξn, dpi; type = :dis)
```

Extract mode shapes using Sdof approximation

**Inputs**

  * `freq`: Frequency vector
  * `H`: Frequency response function
  * `fn`: Natural frequencies
  * `ξn`: Damping ratios
  * `dpi`: Driving point indices

      * `dpi[1]`: Driving point index on the measurement mesh
      * `dpi[2]`: Driving point index on the excitation mesh
  * `method`: Method to extract the mode shapes

      * `PeakPicking`: Peak picking method (default)
      * `CircleFit`: Circle fitting method
  * `type`: Type of FRF used to extract the natural frequencies and damping ratios

      * `:dis`: Admittance (default)
      * `:vel`: Mobility
      * `:acc`: Accelerance

**Output**

  * `ϕn`: Mode shapes

**Note** If the number of measurement points is less than the number of excitation points, the mode shapes are estimated at the excitation points (roving hammer test). Otherwise, the mode shapes are estimated at the measurement points (roving accelerometer test).
