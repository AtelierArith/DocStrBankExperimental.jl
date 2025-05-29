```
freq_extraction(freq, H, method::SdofModalExtraction; type = :dis)
```

Extract natural frequencies and damping ratios from the Bode diagram fitting method

**Inputs**

  * `freq`: Frequency vector
  * `H`: Frequency response function
  * `method`: Method to extract the natural frequencies and damping ratios

      * `PeakPicking`: Peak picking method (default)
      * `CircleFit`: Circle fitting method
  * `type`: Type of FRF used to extract the natural frequencies and damping ratios

      * `:dis`: Admittance (default)
      * `:vel`: Mobility
      * `:acc`: Accelerance

**Outputs**

  * `fn`: Natural frequencies
  * `ξn`: Damping ratios

**Note** It is supposed that `H` is a row or a column of the FRF, meaning that H is a Vector
