```
compute_FTLE!(FTLE::ScalarGridData, final_x::ScalarGridData, final_y::ScalarGridData, dx::Real, dy::Real, T::Real)
```

Compute the `FTLE` field given the final positions of initial points on a collocated grid. 

The underlying math is detailed in: https://shaddenlab.berkeley.edu/uploads/LCS-tutorial/computation.html. For each grid point, first compute the gradient of the flow map using two point central differencing. Then, calculate the maximum eigenvalue of the 2 x 2 gradient matrix. Finally, compute the FTLE value using the eigenvalue.

# Arguments

  * `FTLE`: will hold the FTLE field, in `ScalarGridData` type
  * `final_x`: deformed x positions, in `ScalarGridData` type
  * `final_y`: deformed y positions, in `ScalarGridData` type
  * `dx`: spacing of initial grids in x
  * `dy`: spacing of initial grids in y
  * `T`: length of integration time
