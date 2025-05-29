```
Mesh(args)
```

Construct a periodic mesh of `N` collocation points regularly spaced between `xmin` (included) and `xmax` (excluded), and associated Fourier modes.

# Arguments

Can be either

  * a `NamedTuple` containing `N` and `xmin` and `xmax`; or
  * a `NamedTuple` containing `N` and `L` (in which case `xmin=-L` and `xmax=L`); or
  * a vector of regularly spaced collocation points.

# Return values

`m=Mesh(args)` is of parametric type and offers with

  * `m.N`: number of collocation points and Fourier modes;
  * `m.xmin`: minimum of the mesh (included in the vector of collocation points);
  * `m.xmax`: maximum of the mesh (excluded in the vector of collocation points);
  * `m.dx`: distance between two collocation points;
  * `m.x`: the vector of collocation points;
  * `m.k`: the vector of wavenumbers;
  * `m.kmin`: minimum of wavenumbers (included in the vector of wavenumbers);
  * `m.kmax`: maximum of wavenumbers (included in the vector of wavenumbers);
  * `m.dk`: distance between two Fourier modes.
