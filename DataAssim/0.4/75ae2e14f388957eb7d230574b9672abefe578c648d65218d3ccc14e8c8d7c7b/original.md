```
Xa,xa = ESTKF(Xf,HXf,y,R,H,...)
```

Computes analysis ensemble `Xa` based on forecast ensemble `Xf` and observations `y` using the ESTKF ensemble scheme.

# Input arguments:

  * `Xf`: forecast ensemble (n x N)
  * `HXf`: the observation operator applied on the ensemble (product H*Xf)
  * `y`: observations (m)
  * `R`: observation error covariance  (m x m).
  * `H`: operator (m x n). Except for the serialEnSRF it is never used and can be empty

# Optional keywords arguments:

  * `debug`: set to true to enable debugging. Default (false) is no debugging.
  * `tolerance`: expected rounding error (default 1e-10) for debugging checks. This is not used if debug is false.

# Output arguments:

  * `Xa`: the analysis ensemble (n x N)
  * `xa`: the analysis ensemble mean (n)

Notations follows: Sangoma D3.1 http://data-assimilation.net/Documents/sangomaDL3.1.pdf
