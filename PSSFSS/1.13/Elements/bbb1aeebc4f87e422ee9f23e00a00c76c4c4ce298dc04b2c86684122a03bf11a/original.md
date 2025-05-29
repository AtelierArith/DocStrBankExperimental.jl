```
pixels(; P, patternmat, units, kwargs...)
```

# Description:

Create a variable of type `RWGSheet` that contains the triangulation for an arbitrarily pixelated square unit cell. The returned value has fields `s₁`, `s₂`, `β₁`, `β₂`, `ρ`, `e1`,  `e2`, `fv`, `fe`, and `fr` properly initialized.  

# Arguments:

All arguments are keyword arguments which can be entered in any order.

## Required arguments:

  * `P::Real > 0`: The side length of the square unit cell, specified in units defined by the `units` keyword argument.
  * `patternmat::AbstractMatrix{<:Integer}`: A square matrix, consisting solely of 1's and 0's. The matrix entries control the metallization pattern in the unit cell, with a 1 or `true` value denoting a metallized pixel, and a 0 or `false` value indicating no metallization.  The `(i,j)` entry corresponds to the pixel centered at `(x,y) = ((j-1/2)d, P-(i-1/2)d)`, where `d = P / size(patternmat, 1)`.
  * `units`:  Length units for `P` (either `mm`, `cm`, `inch`, or `mil`).

## Optional arguments:

  * `pdiv::Int = 1`: The number of "chops" or subdivisions applied to each square pixel side when forming the geometry triangulation. A value of `1` (the default) means that the pixels are not subdivided any further, except for a single diagonal across each  pixel to form triangles.  A value of `2` would subdivide each pixel into 4 squares.  A diagonal edge would be added to each of the resulting squares to form triangles.
  * `quad::Bool=false`:  If `true`, each subpixel (or pixel, if `pdiv` is 1) is divided into four triangles by adding two diagonals.  If `false` (the default), only a single diagonal is added to produce two triangles.
  * `sym::Bool = false`: A `true` value states that the pixel matrix has vertical and horizontal mirror symmetry, and  consists of an even number of rows (and columns).  If `true`, the diagonals added to the squares to form  triangles will exhibit the same left-right and up-down mirror symmetry as the collection of `true` (`false`) pixel locations.  If `sym=false` and `quad=false`, then all added diagonals across the unit cell will have the same  orientation.  `sym` has no effect (i.e. is redundant) if `quad=true` since  in that case the two added diagonals already ensure mirror symmetry of the triangulation.
  * `class::Char='M'`  Specify the class, either `'J'` or `'M'`. If `'J'`, the unknowns are electric surface  currents in the areas corresponding to `1` values of the pixels.  If `'M'`,  the unknowns are magnetic surface currents in the areas corresponding to `0` values of the pixels.  It is known that using `'J'` can result in  grossly incorrect results for some geometries where adjacent metallic pixels intersect at only a single point. Therefore, use of only `'M'` is strongly recommended for most `pixels` elements and all `sympixels` elements.
  * `dx::Real=0.0`, `dy::Real=0.0`:  These specify the offsets in the x and y directions applied to the entire           unit cell and its contents.  Length units are as specified in the `units` keyword.
  * `rot::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the entire unit cell and its contents.           This rotation is applied prior to any offsets specified in `dx` and `dy`.
  * `Zsheet::Complex=0.0`:  The frequency-independent surface impedance of the FSS conductor in  units of [Ω].  May only be specified for a sheet of class `'J'`.  If `Zsheet` is specified, then  `sigma` (or `σ`) may not be specified.                          )
  * `sigma` or `σ`: DC, bulk conductivity [S/m].  Only allowed for sheets of class `'J'`.  Cannot be  simultaneously specified with `Zsheet`.  Is used with `Rq` by PSSFSS to calculate an effective  sheet surface impedance at each frequency, using the Gradient Model (Grujić 2022).
  * `Rq=0.0`: RMS surface roughness [m].  Only legal for class `'J'`. Only used if `sigma` (or `σ`) is   also specified.  In that case is is used along with `sigma` to calculate a frequency-dependent  sheet impedance using the Gradient Model.  The default value of 0 denotes a smooth surface.
  * `disttype::Symbol=:normal`: Probability distrubution type for surface roughness.  defaults to `:normal`.  The other legal value is `:rayleigh`.
  * `fufp::Bool`:  This keyword is not usually required.  `fufp` is mnemonic for "Find Unique Face Pairs".  If true, the code will search the  triangulation for classes of triangle pairs that are the equivalent in the toeplitz sense.  I.e., if triangle pairs (A,B) and (C,D) belong to the same equivalence class,  the six vertices in the pair (A,B) can be made to coincide  with those of pair (C,D) by a simple translation. If there are many such equivalent pairs,  a significant decrease in matrix fill time ensues by exploiting the equivalence.  The tradeoff is the time needed to identify them.  The default value is `true` for the `strip`, `diagstrip`,   `meander`, `manji`, `loadedcross`, `jerusalemcross`, `pixels`, 4-sided `polyring` styles (those  employing structured meshes), and `sympixels`, and `false` for the remaining styles (those employing unstructured meshes).
