```
Xa,xa = local_EnKF(Xf,H,y,diagR,part,selectObs,...)
```

Computes analysis ensemble `Xa` based on forecast ensemble `Xf` using the observation `y` using the local EnKF.

## Inputs:

  * `Xf`: forecast ensemble (n x N)
  * `H`: observation operator (m x n)
  * `y`: observation (m x 1)
  * `diagR`: diagonal of the observation error covariance R (m x 1)
  * `part`: vector of integer "labels". Every element of the state vector with the same number belong to the same subdomain
  * `selectObs`: callback routine to select observations with a within a subdomain. As input is takes an integer representing the index of the state vector and returns a vector of weights (m x 1). For example:

```
     selectObs(i) = exp(- ((x[i] - xobs[:]).^2 + (y(i) - yobs[:]).^2)/L^2 );
```

or

```
     selectObs(i) = compact_locfun(L,...
         sqrt((x[i] - xobs[:]).^2 + (y[i] - yobs[:]).^2));
```

where `x` and `y` is the horizontal model grid, `xobs` and `yobs` are the locations of the observations and `L` is a correlation length-scale

## Optional inputs:

  * `display`: if true, then display progress (false is the default)
  * `minweight`: analysis is performed using observations for which  weights is larger than minweight. (default 1e-8)
  * `HXf`: if non empty, then it is the product `H*Xf`. In this case, `H` is not  used

## Output:

  * `Xa`: the analysis ensemble (n x N)
  * `xa``: the analysis ensemble mean (n x 1)

See also: compact_locfun
