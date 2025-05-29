```
SdofFRFProblem(sdof, freq, type_exc, type_resp)
```

Structure containing the data for computing the FRF a sdof system

**Fields**

  * `sdof::Sdof`: Sdof structure
  * `freq::AbstractRange`: Vector of frequencies [Hz]
  * `type_exc::Symbol`: Type of excitation

      * `:force`: External force (default)
      * `:base`: Base motion
  * `type_resp::Symbol`: Type of response

      * `:dis`: Admittance (default)
      * `:vel`: Mobility
      * `:acc`: Accelerance
