```
polyring(;s1::Vector, s2::Vector, a::Vector, b::Vector, sides::Int ,ntri::Int ,orient::Real, units::PSSFSSLength, kwargs...) --> RWGSheet
```

Return a variable of type `RWGSheet` that contains the triangulation for one or more concentric annular regions bounded by polygons.

# Arguments:

All arguments are keyword arguments which can be entered in any order.

## Required arguments:

  * `units`:  Length units (`mm`, `cm`, `inch`, or `mil`)
  * `s1` and `s2`:  2-vectors containing the unit cell lattice vectors.
  * `a` and `b`:  n-vectors (n>=1) of the same length providing the inner and outer radii, respectively of the polygonal rings. Entries in `a` and `b` must be strictly increasing, except for possibly `b[end]` as discussed  below. `b[i] > a[i]` ∀ `i ∈ 1:n`, except possibly `b[end]` as discussed below.  `a[1]` may be zero to denote a solid (non-annular) polygon as the first "ring". It is possible to let the outermost ring to extend completely to the unit cell boundary.   This is specified by setting `b[end]` < 0, in which case for unstructured meshes, `-b[end]` is interpreted as the number of edges along the shorter of the `s1` and `s2` lattice vectors.
  * `sides`:  The number (>= 3) of polygon sides.
  * `ntri`:  The desired total number of triangles distributed among all the annular regions. This is a guide, the actual number  will likely be different.

## Optional arguments:

  * `orient::Real=0.0`:  Counterclockwise rotation angle in degrees used to locate the initial          vertex of the polygonal rings.  The default is to locate the vertex on the          positive x-axis.
  * `structuredtri::Bool`: Defaults to `true` when `sides==4` and false otherwise. A `true` value is only allowed when `sides==4` and `s1` ⟂ `s2`.  If true, use a structured mesh for the triangulation.  If false, the unstructured mesh generator that was standard up to PSSFSS version 1.2 will be used. A structured  mesh can be analyzed more efficiently, but the number of triangles created by the unstructured mesh generator is usually closer to `ntri` than the number for the structured mesh generator.
  * `class::Char='J'`  Specify the class, either `'J'` or `'M'`.. If `'J'`,  the unknowns are electric surface           currents, as used to model a wire or metallic patch-type FSS.  If `'M'`,  the unknowns are          magnetic surface currents, as used to model a slot or aperture in a perfectly conducting plane.
  * `dx::Real=0.0`, `dy::Real=0.0`:  These specify the offsets in the x and y directions applied to the entire           unit cell and its contents.  Length units are as specified in the `units` keyword.
  * `rot::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the entire unit cell and its contents.           This rotation is applied prior to any offsets specified in `dx` and `dy`.
  * `Zsheet::Complex=0.0`:  The frequency-independent surface impedance of the FSS conductor in  units of [Ω].  May only be specified for a sheet of class `'J'`.  If `Zsheet` is specified, then  `sigma` (or `σ`) may not be specified.                          )
  * `sigma` or `σ`: DC, bulk conductivity [S/m].  Only allowed for sheets of class `'J'`.  Cannot be  simultaneously specified with `Zsheet`.  Is used with `Rq` by PSSFSS to calculate an effective  sheet surface impedance at each frequency, using the Gradient Model (Grujić 2022).
  * `Rq=0.0`: RMS surface roughness [m].  Only legal for class `'J'`. Only used if `sigma` (or `σ`) is   also specified.  In that case is is used along with `sigma` to calculate a frequency-dependent  sheet impedance using the Gradient Model.  The default value of 0 denotes a smooth surface.
  * `disttype::Symbol=:normal`: Probability distrubution type for surface roughness.  defaults to `:normal`.  The other legal value is `:rayleigh`.
  * `fufp::Bool`:  This keyword is not usually required.  `fufp` is mnemonic for "Find Unique Face Pairs".  If true, the code will search the  triangulation for classes of triangle pairs that are the equivalent in the toeplitz sense.  I.e., if triangle pairs (A,B) and (C,D) belong to the same equivalence class,  the six vertices in the pair (A,B) can be made to coincide  with those of pair (C,D) by a simple translation. If there are many such equivalent pairs,  a significant decrease in matrix fill time ensues by exploiting the equivalence.  The tradeoff is the time needed to identify them.  The default value is `true` for the `strip`, `diagstrip`,   `meander`, `manji`, `loadedcross`, `jerusalemcross`, `pixels`, 4-sided `polyring` styles (those  employing structured meshes), and `sympixels`, and `false` for the remaining styles (those employing unstructured meshes).
