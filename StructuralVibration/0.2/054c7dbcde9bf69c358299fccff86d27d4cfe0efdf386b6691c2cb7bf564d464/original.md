```
srs(base_acc::ArbitraryExc, freq, t, ξ = 0.05,
    type = (instance = :primary, amplitude = :abs), alg = :Smallwood)
```

Compute the Shock Response Spectrum (SRS)

**Inputs**

  * `base_acc::ArbitraryExc`: Base acceleration type - see `excitation` function for detatils
  * `freq`: Vector of frequencies [Hz]
  * `t`: Time points at which to evaluate the response
  * `ξ`: Damping ratio (default = 0.05)
  * `type`: Type of SRS

      * `instance`: Instance of the SRS

          * `:primary`: Primary instance (default)
          * `:secondary`: Secondary instance
      * `amplitude`: Amplitude used of the computing SRS

          * `:abs`: Maximum absolute amplitude (default)
          * `:pos`: Maximum positive amplitude
          * `:neg`: Maximum negative amplitude
  * `alg`: Algorithm to compute the SRS

      * `:Basic`: Basic algorithm
      * `:RecursiveInt`: Recursive integration algorithm
      * `:RecursiveFilt`: Recursive filtering algorithm
      * `:Smallwood`: Smallwood algorithm (default)

**Output**

  * `srs`: Vector of the SRS values

*Note*

  * Primary instance - response of the system during the application of the base acceleration
  * Secondary instance - response of the system after the application of the base acceleration
