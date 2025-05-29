```
function manji(; L1, L2, L3, w, s1, s2, ntri, units, a=0, w2=0, CCW=false, orient=0, kwargs...)
```

# Description:

Create a variable of type `RWGSheet` that contains the triangulation for a "manji" (Japanese for swastica shape) type of geometry. The returned value has fields `s₁`, `s₂`, `β₁`, `β₂`, `ρ`, `e1`, `e2`, `fv`, `fe`,  and `fr` properly initialized.

# Arguments:

All arguments are keyword arguments which can be entered in any order.

## Required arguments:

  * `L1`, `L2`, `L3`, `w`: Geometrical parameters defined in the diagram at ![https://simonp0420.github.io/PSSFSS.jl/stable/assets/manjidef.png](https://simonp0420.github.io/PSSFSS.jl/stable/assets/manjidef.png) Note that if `a` ≤ `w` then the center square shown in the figure will not be present.  Similarly, if  `L3` ≤ `2*w` then the bent portions of the arms will consist of a single strip of width `L3`  (without any gap in the middle).
  * `s1` and `s2`:  2-vectors containing the unit cell lattice vectors.
  * `units`:  Length units (`mm`, `cm`, `inch`, or `mil`)
  * `ntri`:  The desired total number of triangles.  This is a guide/request,  the actual number will likely be different.

## Optional arguments:

  * `a::Real=0`: A geometrical parameter defined in the above referenced diagram.  If `a` ≤ `w` then the center square shown in that figure will be absent, and the arms will continue uninterrupted to the center of the structure.
  * `w2::Real=0`: The width of the square ring border shown in  the above-referenced diagram.  If `w2` ≤ 0 the square ring will not be included in the triangulation. Note that `w2 > 0` is only allowed for square unit cells.
  * `L4`: The outer side length of the square ring border.  `0 < L4 ≤ norm(s1)`. If not specified, when `w2 > 0`, the default value for `L4` is the unit cell square dimension. It is the user's  responsibility to ensure that `L4` is large enough to prevent the square ring from interfering with other parts of the `manji` structure.
  * `CCW::Bool=false`: By default, the chiral structure has a clockwise sense.  If  `CCW` is `true`, the structure will be counter-clockwise.
  * `orient::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the structure within the unrotated unit cell.  Note that the outer square ring present when `w2 > 0` will not be rotated by use of a nonzero `orient` value.
  * `class::Char='J'`  Specify the class, either `'J'` or `'M'`.. If `'J'`,  the unknowns are electric surface           currents, as used to model a wire or metallic patch-type FSS.  If `'M'`,  the unknowns are          magnetic surface currents, as used to model a slot or aperture in a perfectly conducting plane.
  * `dx::Real=0.0`, `dy::Real=0.0`:  These specify the offsets in the x and y directions applied to the entire           unit cell and its contents.  Length units are as specified in the `units` keyword.
  * `rot::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the entire unit cell and its contents.           This rotation is applied prior to any offsets specified in `dx` and `dy`.
  * `Zsheet::Complex=0.0`:  The frequency-independent surface impedance of the FSS conductor in  units of [Ω].  May only be specified for a sheet of class `'J'`.  If `Zsheet` is specified, then  `sigma` (or `σ`) may not be specified.                          )
  * `sigma` or `σ`: DC, bulk conductivity [S/m].  Only allowed for sheets of class `'J'`.  Cannot be  simultaneously specified with `Zsheet`.  Is used with `Rq` by PSSFSS to calculate an effective  sheet surface impedance at each frequency, using the Gradient Model (Grujić 2022).
  * `Rq=0.0`: RMS surface roughness [m].  Only legal for class `'J'`. Only used if `sigma` (or `σ`) is   also specified.  In that case is is used along with `sigma` to calculate a frequency-dependent  sheet impedance using the Gradient Model.  The default value of 0 denotes a smooth surface.
  * `disttype::Symbol=:normal`: Probability distrubution type for surface roughness.  defaults to `:normal`.  The other legal value is `:rayleigh`.
  * `fufp::Bool`:  This keyword is not usually required.  `fufp` is mnemonic for "Find Unique Face Pairs".  If true, the code will search the  triangulation for classes of triangle pairs that are the equivalent in the toeplitz sense.  I.e., if triangle pairs (A,B) and (C,D) belong to the same equivalence class,  the six vertices in the pair (A,B) can be made to coincide  with those of pair (C,D) by a simple translation. If there are many such equivalent pairs,  a significant decrease in matrix fill time ensues by exploiting the equivalence.  The tradeoff is the time needed to identify them.  The default value is `true` for the `strip`, `diagstrip`,   `meander`, `manji`, `loadedcross`, `jerusalemcross`, `pixels`, 4-sided `polyring` styles (those  employing structured meshes), and `sympixels`, and `false` for the remaining styles (those employing unstructured meshes).
