```
compute_FTLE!(FTLE, nx, ny, T, final_positions, dx, dy)
```

Compute the `FTLE` field given the final positions of initial points on a collocated grid. 

The underlying math is detailed in: https://shaddenlab.berkeley.edu/uploads/LCS-tutorial/computation.html. For each grid point, first compute the gradient of the flow map using two point central differencing. Then, calculate the maximum eigenvalue of the 2 x 2 gradient matrix. Finally, compute the FTLE value using the eigenvalue.

# Arguments

  * `FTLE`: an empty 2D array (i.e., `FTLE = zeros(Float64, ny - 2, nx - 2))`, `nx - 2` and `ny - 2` accounts for the boundary points in the central difference formula
  * `nx`: number of grid points in x
  * `ny`: number of grid points in y
  * `T`: length of integration time
  * `final_positions`: solutions of the IVP
  * `dx`: spacing of initial grids in x
  * `dy`: spacing of initial grids in y
