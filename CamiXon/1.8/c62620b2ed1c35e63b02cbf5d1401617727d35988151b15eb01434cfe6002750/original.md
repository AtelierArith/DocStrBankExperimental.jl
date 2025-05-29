```
autoGrid(atom::Atom, T::Type; p=0, rmax=0, nmax=0, N=0, polynom=[], epn=5, k=5, msg=false)
```

Automatic setting of grid parameters for a given orbit [`Orbit`](@ref) or an array of orbits - `orbits = [orbit1, orbit2, ⋯]`. Important cases:

  * `p == 0` (exponential radial grid)
  * `p == 1` (linear radial grid)
  * `p > 1` (quasi-exponential radial grid)
  * `polynom=[]` (free polynomial grid based on the `polynom`)
  * `Nboost` (multiplier to boost numerical precision)
  * `epn` (endpoint number: odd number to be used for trapezoidal integration with endpoint correction)
  * `k` (Adams-Moulton order to be used for `k+1`-point Adams-Moulton integration)

#### Example:

```
julia> atom = castAtom(;Z=1, A=1, Q=0, msg=false);

julia> spinorbit = castSpinorbit(n=75, ℓ=0, msg=false);

julia> grid = autoGrid(atom, Float64; nmax=spinorbit.n, msg=true);
Grid: exponential, Float64, rmax = 14137.5, N = 7900, h = 0.00126582, r0 = 0.642684

plot_gridfunction(grid, 1:grid.N; title="")
```

The plot is made using CairomMakie. NB.: `plot_gridfunction` is not part of the `CamiXon` package. ![Image](../../assets/exponential_grid.png)
