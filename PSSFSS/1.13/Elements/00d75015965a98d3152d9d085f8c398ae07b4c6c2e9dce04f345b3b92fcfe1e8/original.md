```
sinuous(; arms, b, w, g, sides, ntri, units, s1, s2, kwargs...) --> RWGSheet
```

Return a variable of type `RWGSheet` representing a sinuous element as shown in this diagram: ![https://simonp0420.github.io/PSSFSS.jl/stable/assets/sinuousdef.png](https://simonp0420.github.io/PSSFSS.jl/stable/assets/sinuousdef.png)

# Arguments:

All arguments are keyword arguments which can be entered in any order.

## Required arguments:

  * `arms::Int`: The number of arms in the structure.
  * `rc::Real > 0`: The radius of the central circle.  `rc` must be greater than or equal to `w`.
  * `b`:  n-vector (n ≥ 1) providing the outer radii of the polygonal rings. Entries must be positive and strictly increasing, with the difference between adjacent rings exceeding `w`.
  * `w`: The width of the traces in the arms.
  * `g`: A scalar containing the rectangular gap width separating adjacent arms.
  * `sides::Int`:  The number (>= 4) of polygon sides for the background regular annular polygon(s) from which the  ring sections are created.
  * `ntri::Int`:  The desired total number of triangles. This is a guide/request, the actual number will likely be different.
  * `units`:  Length units (`mm`, `cm`, `inch`, or `mil`)
  * `s1` and `s2`:  2-vectors containing the unit cell lattice vectors.

## Optional arguments:

  * `orient::Real=0.0`:  Counterclockwise rotation angle in degrees used to locate center of the first arm.
  * `w2::Real=0.0`: The trace width of the enclosing square loop "rim".  Note that `w2 > 0` is only permitted for a square unit cell.
  * `L2`: The outer dimension (i.e. the full side length) of the square "rim" present when `w2 > 0`.  The user is responsible for choosing `L2` large enough that the rim does not intefere with the sinuous arms of the structure.  `L2` must be less than or equal to the square unit cell dimension.  It defaults to the unit cell dimension if it is not specified.
  * `c2::Real=0.0`: The outer dimension of the small squares shown in the corners of the enclosing square loop "rim". If  `c2==0` then the squares are not included, and the outer loop is a simple square loop.
  * `class::Char='J'`  Specify the class, either `'J'` or `'M'`.. If `'J'`,  the unknowns are electric surface           currents, as used to model a wire or metallic patch-type FSS.  If `'M'`,  the unknowns are          magnetic surface currents, as used to model a slot or aperture in a perfectly conducting plane.
  * `dx::Real=0.0`, `dy::Real=0.0`:  These specify the offsets in the x and y directions applied to the entire           unit cell and its contents.  Length units are as specified in the `units` keyword.
  * `rot::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the entire unit cell and its contents.           This rotation is applied prior to any offsets specified in `dx` and `dy`.
  * `Zsheet::Complex=0.0`:  The frequency-independent surface impedance of the FSS conductor in  units of [Ω].  May only be specified for a sheet of class `'J'`.  If `Zsheet` is specified, then  `sigma` (or `σ`) may not be specified.                          )
  * `sigma` or `σ`: DC, bulk conductivity [S/m].  Only allowed for sheets of class `'J'`.  Cannot be  simultaneously specified with `Zsheet`.  Is used with `Rq` by PSSFSS to calculate an effective  sheet surface impedance at each frequency, using the Gradient Model (Grujić 2022).
  * `Rq=0.0`: RMS surface roughness [m].  Only legal for class `'J'`. Only used if `sigma` (or `σ`) is   also specified.  In that case is is used along with `sigma` to calculate a frequency-dependent  sheet impedance using the Gradient Model.  The default value of 0 denotes a smooth surface.
  * `disttype::Symbol=:normal`: Probability distrubution type for surface roughness.  defaults to `:normal`.  The other legal value is `:rayleigh`.
  * `fufp::Bool`:  This keyword is not usually required.  `fufp` is mnemonic for "Find Unique Face Pairs".  If true, the code will search the  triangulation for classes of triangle pairs that are the equivalent in the toeplitz sense.  I.e., if triangle pairs (A,B) and (C,D) belong to the same equivalence class,  the six vertices in the pair (A,B) can be made to coincide  with those of pair (C,D) by a simple translation. If there are many such equivalent pairs,  a significant decrease in matrix fill time ensues by exploiting the equivalence.  The tradeoff is the time needed to identify them.  The default value is `true` for the `strip`, `diagstrip`,   `meander`, `manji`, `loadedcross`, `jerusalemcross`, `pixels`, 4-sided `polyring` styles (those  employing structured meshes), and `sympixels`, and `false` for the remaining styles (those employing unstructured meshes).
