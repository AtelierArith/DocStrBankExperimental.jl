```
Exact <: Method
```

Solves the system exactly. This is only implemented for specific systems.

Right now, the implemented exact methods are

  * three-dimensional single-component system of hard spheres with the Percus Yevick closure [1]
  * three-dimensional multi-component system of additive hard spheres with the Percus Yevick closure [2]
  * one-dimensional single-component system of hard spheres with the Percus Yevick closure [3]
  * five-dimensional single-component system of hard spheres with the Percus Yevick closure [3]

Construct using 

`Exact(;  M=1000, dr = 10.0/M)`

Here, `M` is the number of points that the exact solution is evaluated on, and `dr` is the grid spacing. These are used to perform Fourier transformations.

Examples

`method = Exact()`

`method = Exact(M=1000)`

`method = Exact(M=1000, dr=0.01)`

References:

1. Wertheim, M. S. "Exact solution of the Percus-Yevick integral equation for hard spheres." Physical Review Letters 10.8 (1963): 321.
2. Baxter, R. J. "Ornstein–Zernike relation and Percus–Yevick approximation for fluid mixtures." The Journal of Chemical Physics 52.9 (1970): 4559-4562.
3. Leutheusser, E. "Exact solution of the Percus-Yevick equation for a hard-core fluid in odd dimensions." Physica A: Statistical Mechanics and its Applications 127.3 (1984): 667-676.
