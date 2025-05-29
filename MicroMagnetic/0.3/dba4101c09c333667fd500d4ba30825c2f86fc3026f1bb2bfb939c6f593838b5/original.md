```
add_exch(sim::AtomisticSim, Jfun::Function; name="exch")
```

Add spatial exchange interaction to the system by accepting a function that defines the exchange parameters at different spatial points.  The function should accept the indices `(i, j, k)` representing the position of the spin on the mesh and return an **array**.  The length of this array should be half the number of neighbors.

For example, for a `CubicMesh`, the function should return an array `[Jx, Jy, Jz]`, where:

  * `Jx` represents the exchange interaction between the site at `(i, j, k)` and the site at `(i+1, j, k)`,
  * `Jy` represents the exchange interaction between the site at `(i, j, k)` and the site at `(i, j+1, k)`,
  * `Jz` represents the exchange interaction between the site at `(i, j, k)` and the site at `(i, j, k+1)`.

The array length corresponds to half the number of neighbors, because exchange interactions are considered only in the positive direction (i.e., the interactions with neighboring sites in increasing index directions).

#### Examples:

```julia
function spatial_J(i, j, k)
    Jx = i < 10 ? 1meV : 2meV
    Jy = 1meV
    Jz = 1meV
    return [Jx, Jy, Jz]  # Returns an array
end

add_exch(sim, spatial_J)
```

In this example:

  * The exchange interaction in the x-direction (`Jx`) depends on the value of `i`. If `i` is less than 10, it is `1meV`, otherwise it is `2meV`.
  * The interactions in the y- and z-directions (`Jy` and `Jz`) are fixed at `1meV`.
