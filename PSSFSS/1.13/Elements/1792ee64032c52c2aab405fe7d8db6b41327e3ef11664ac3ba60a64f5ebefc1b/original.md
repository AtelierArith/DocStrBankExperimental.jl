```
splitring(; s1, s2, a, b, sides, ntri, gapwidth, gapcenter, gapangle, units, kwargs...) --> RWGSheet
```

Return a variable of type `RWGSheet` similar to a `polyring` but with zero or more gaps in each concentric annular region.

# Arguments:

All arguments are keyword arguments which can be entered in any order.

## Required arguments:

  * `units`:  Length units (`mm`, `cm`, `inch`, or `mil`)
  * `s1` and `s2`:  2-vectors containing the unit cell lattice vectors.
  * `a` and `b`:  n-vectors (n>=1) of the same length providing the inner and outer radii, respectively of the polygonal rings. Entries in `a` and `b` must be positive and strictly increasing. `b[i] > a[i]` ∀ `i ∈ 1:n`.
  * `sides`:  The number (>= 4) of polygon sides for the background regular annular polygon(s) from which the gaps are removed.
  * `gapcenter`: A scalar or vector of angles in degrees that define the gap center angular location(s), measured counterclockwise.   A scalar implies that all rings have a gap in that same angular location.  If a vector, then it must have the  same length as `a` and `b`, with `gapcenter[m]` denoting the gap center location for the `m`th ring. However `gapcenter[m]` can be either a scalar (denoting a single gap) or an n-tuple (denoting n gaps  in the `m`th ring).
  * `gapwidth`: A scalar or a vector of the same length as `a` and `b` containing the gap width(s) for each ring. A width of zero implies that the ring is not split (i.e. there is no gap).  If the `gapwidth` of all rings is zero, then the resulting geometry is similar to a `polyring`. If a ring is to have multiple gaps, then the widths of the gaps for that ring should be passed as a tuple.  For example, suppose there are three rings and the second ring has 2 gaps, with the others having a single gap.  Then `gapwidth = [0.5, (0.4, 0.6), 0.3]` would be an appropriately formatted input in this case. When `gapwidth` is specified, the gaps are implemented as if a rectangular region is removed from the annular polygonal rings. Note that only  one of `gapwidth` and `gapangle` can be specified.
  * `gapangle`: A scalar or vector of the same length as `a` and `b` containing the angular widths of the gaps in degrees. As with `gapwidth`, for any rings with multiple gaps, the corresponding entry in `gapangle` should be a  tuple of the same length as the number of gaps for that ring. When `gapangle` is specified, the gap(s)  in the `m`th ring is/are formed as if pie-shaped wedge(s) with wedge angle(s) `gapangle[m]`, are  removed from the ring(s). The locations and sizes of the tuples in `gapangle` must agree with those  in `gapcenter`.  Note that only one of `gapangle` and `gapwidth` can be specified.
  * `ntri`:  The desired total number of triangles distributed among all the annular regions. This is a guide, the actual number  will likely be different.

## Optional arguments:

  * `orient::Real=0.0`:  Counterclockwise rotation angle in degrees used to locate the initial vertex of the polygonal rings.  The default is to locate the vertex on the ray from the center parallel to the positive x-axis.
  * `class::Char='J'`  Specify the class, either `'J'` or `'M'`.. If `'J'`,  the unknowns are electric surface           currents, as used to model a wire or metallic patch-type FSS.  If `'M'`,  the unknowns are          magnetic surface currents, as used to model a slot or aperture in a perfectly conducting plane.
  * `dx::Real=0.0`, `dy::Real=0.0`:  These specify the offsets in the x and y directions applied to the entire           unit cell and its contents.  Length units are as specified in the `units` keyword.
  * `rot::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the entire unit cell and its contents.           This rotation is applied prior to any offsets specified in `dx` and `dy`.
  * `Zsheet::Complex=0.0`:  The frequency-independent surface impedance of the FSS conductor in  units of [Ω].  May only be specified for a sheet of class `'J'`.  If `Zsheet` is specified, then  `sigma` (or `σ`) may not be specified.                          )
  * `sigma` or `σ`: DC, bulk conductivity [S/m].  Only allowed for sheets of class `'J'`.  Cannot be  simultaneously specified with `Zsheet`.  Is used with `Rq` by PSSFSS to calculate an effective  sheet surface impedance at each frequency, using the Gradient Model (Grujić 2022).
  * `Rq=0.0`: RMS surface roughness [m].  Only legal for class `'J'`. Only used if `sigma` (or `σ`) is   also specified.  In that case is is used along with `sigma` to calculate a frequency-dependent  sheet impedance using the Gradient Model.  The default value of 0 denotes a smooth surface.
  * `disttype::Symbol=:normal`: Probability distrubution type for surface roughness.  defaults to `:normal`.  The other legal value is `:rayleigh`.
  * `fufp::Bool`:  This keyword is not usually required.  `fufp` is mnemonic for "Find Unique Face Pairs".  If true, the code will search the  triangulation for classes of triangle pairs that are the equivalent in the toeplitz sense.  I.e., if triangle pairs (A,B) and (C,D) belong to the same equivalence class,  the six vertices in the pair (A,B) can be made to coincide  with those of pair (C,D) by a simple translation. If there are many such equivalent pairs,  a significant decrease in matrix fill time ensues by exploiting the equivalence.  The tradeoff is the time needed to identify them.  The default value is `true` for the `strip`, `diagstrip`,   `meander`, `manji`, `loadedcross`, `jerusalemcross`, `pixels`, 4-sided `polyring` styles (those  employing structured meshes), and `sympixels`, and `false` for the remaining styles (those employing unstructured meshes).
