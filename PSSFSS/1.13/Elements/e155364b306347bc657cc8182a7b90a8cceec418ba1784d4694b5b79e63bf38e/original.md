```
rectstrip(;Lx::Real, Ly::Real, Nx::Int, Ny::Int, Px::Real, Py::Real, units::PSSFSSLength, kwargs...)
```

Return a variable of type `RWGSheet` that contains the triangulation for a rectangular strip.

# Arguments:

All arguments are keyword arguments which can be entered in any order.

## Required arguments:

  * `units`:  Length units (`mm`, `cm`, `inch`, or `mil`)
  * `Lx` and `Ly`:  Lengths of the strip in the x and y directions.
  * `Px` and `Py`:  Lengths (periods) of the rectangular unit cell in the x and y directions.
  * `Nx` and `Ny`:  Number of line segments in the x and y directions, for dividing up the strip into rectangles, which are  triangulated by adding a diagonal to each rectangle.

## Optional arguments:

  * `orient::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the strip within the unrotated unit cell.   This rotation is applied prior to any offsets specified in `dx` and `dy` and any unit cell rotation specified  by `rot`.
  * `class::Char='J'`  Specify the class, either `'J'` or `'M'`.. If `'J'`,  the unknowns are electric surface           currents, as used to model a wire or metallic patch-type FSS.  If `'M'`,  the unknowns are          magnetic surface currents, as used to model a slot or aperture in a perfectly conducting plane.
  * `dx::Real=0.0`, `dy::Real=0.0`:  These specify the offsets in the x and y directions applied to the entire           unit cell and its contents.  Length units are as specified in the `units` keyword.
  * `rot::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the entire unit cell and its contents.           This rotation is applied prior to any offsets specified in `dx` and `dy`.
  * `Zsheet::Complex=0.0`:  The frequency-independent surface impedance of the FSS conductor in  units of [Ω].  May only be specified for a sheet of class `'J'`.  If `Zsheet` is specified, then  `sigma` (or `σ`) may not be specified.                          )
  * `sigma` or `σ`: DC, bulk conductivity [S/m].  Only allowed for sheets of class `'J'`.  Cannot be  simultaneously specified with `Zsheet`.  Is used with `Rq` by PSSFSS to calculate an effective  sheet surface impedance at each frequency, using the Gradient Model (Grujić 2022).
  * `Rq=0.0`: RMS surface roughness [m].  Only legal for class `'J'`. Only used if `sigma` (or `σ`) is   also specified.  In that case is is used along with `sigma` to calculate a frequency-dependent  sheet impedance using the Gradient Model.  The default value of 0 denotes a smooth surface.
  * `disttype::Symbol=:normal`: Probability distrubution type for surface roughness.  defaults to `:normal`.  The other legal value is `:rayleigh`.
  * `fufp::Bool`:  This keyword is not usually required.  `fufp` is mnemonic for "Find Unique Face Pairs".  If true, the code will search the  triangulation for classes of triangle pairs that are the equivalent in the toeplitz sense.  I.e., if triangle pairs (A,B) and (C,D) belong to the same equivalence class,  the six vertices in the pair (A,B) can be made to coincide  with those of pair (C,D) by a simple translation. If there are many such equivalent pairs,  a significant decrease in matrix fill time ensues by exploiting the equivalence.  The tradeoff is the time needed to identify them.  The default value is `true` for the `strip`, `diagstrip`,   `meander`, `manji`, `loadedcross`, `jerusalemcross`, `pixels`, 4-sided `polyring` styles (those  employing structured meshes), and `sympixels`, and `false` for the remaining styles (those employing unstructured meshes).
