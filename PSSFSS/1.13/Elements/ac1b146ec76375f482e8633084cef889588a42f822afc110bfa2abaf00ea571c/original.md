```
meander(;a::Real, b::Real, h::Real, w1::Real, w2::Real, ntri::Int,
              units::PSSFSSLength, orient=0, kwarg...) --> sheet::RWGSheet
```

# Description:

Return a variable of type `RWGSheet` that contains the triangulation for  a meanderline strip.  The returned `sheet` has the components `s₁`, `s₂`,  `β₁`, `β₂`, `ρ`, `e1`, `e2`, `fv`, `fe`, and `fr` properly initialized.   Geometrical parameters are shown in the following diagram:

```
  - - - - - - - - - - - - - - - - - - - - - - - - -             ^
 |                                                |             |
 |                                                |             |
 |                                                |             |
 |                                                |             |
 |                                                |             |
 |            <-------- a/2 ------->              |             |
 |               (center-to-center)               |             |
 |                                                |             |
 |          ----------------------------          |  ^    ^     b
 |          |                          |          |  w2   |     |
 |          |                          |          |  |    |     |
 |          | -----------------------  |          |  v    |     |
 |          | |                     |  |          |             |
 |       -->| |<--w1           w1-->|  |<--       |       h     |
 ------------ |                     |  ------------  ^          |
 |            |                     |             |  w2   |     |
 |            |                     |             |  |    |     |
 ------------ - - - - - - - - - - - ---------------  v    v     v

 <-------------------- a ------------------------->
```

`a` and `b` are unit cell dimensions.  `w1` and `w2` are the widths    of the vertical and horizontal strips, resp. `h` is the total    height of the meander. 

A nicer diagram: ![https://simonp0420.github.io/PSSFSS.jl/stable/assets/meanderdef.png](https://simonp0420.github.io/PSSFSS.jl/stable/assets/meanderdef.png)

# Arguments:

All arguments are keyword arguments which can be entered in any order.

## Required arguments:

  * `a`,`b`,`h`,`w1`, `w2`: Geometrical parameters as defined above.
  * `units`:  Length units (`mm`, `cm`, `inch`, or `mil`)
  * `ntri`:  The desired total number of triangles.  This is a guide, the actual number will likely be different.

## Optional arguments:

  * `orient::Real=0.0`:  Counterclockwise rotation angle in degrees used to rotate the  meanderline orientation within the unrotated unit cell.  Nonzero values are allowed only when the unit cell is a square (i.e. `a` == `b`).  The only allowable values are positive or negative multiples of 90.
  * `class::Char='J'`  Specify the class, either `'J'` or `'M'`.. If `'J'`,  the unknowns are electric surface           currents, as used to model a wire or metallic patch-type FSS.  If `'M'`,  the unknowns are          magnetic surface currents, as used to model a slot or aperture in a perfectly conducting plane.
  * `dx::Real=0.0`, `dy::Real=0.0`:  These specify the offsets in the x and y directions applied to the entire           unit cell and its contents.  Length units are as specified in the `units` keyword.
  * `rot::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the entire unit cell and its contents.           This rotation is applied prior to any offsets specified in `dx` and `dy`.
  * `Zsheet::Complex=0.0`:  The frequency-independent surface impedance of the FSS conductor in  units of [Ω].  May only be specified for a sheet of class `'J'`.  If `Zsheet` is specified, then  `sigma` (or `σ`) may not be specified.                          )
  * `sigma` or `σ`: DC, bulk conductivity [S/m].  Only allowed for sheets of class `'J'`.  Cannot be  simultaneously specified with `Zsheet`.  Is used with `Rq` by PSSFSS to calculate an effective  sheet surface impedance at each frequency, using the Gradient Model (Grujić 2022).
  * `Rq=0.0`: RMS surface roughness [m].  Only legal for class `'J'`. Only used if `sigma` (or `σ`) is   also specified.  In that case is is used along with `sigma` to calculate a frequency-dependent  sheet impedance using the Gradient Model.  The default value of 0 denotes a smooth surface.
  * `disttype::Symbol=:normal`: Probability distrubution type for surface roughness.  defaults to `:normal`.  The other legal value is `:rayleigh`.
  * `fufp::Bool`:  This keyword is not usually required.  `fufp` is mnemonic for "Find Unique Face Pairs".  If true, the code will search the  triangulation for classes of triangle pairs that are the equivalent in the toeplitz sense.  I.e., if triangle pairs (A,B) and (C,D) belong to the same equivalence class,  the six vertices in the pair (A,B) can be made to coincide  with those of pair (C,D) by a simple translation. If there are many such equivalent pairs,  a significant decrease in matrix fill time ensues by exploiting the equivalence.  The tradeoff is the time needed to identify them.  The default value is `true` for the `strip`, `diagstrip`,   `meander`, `manji`, `loadedcross`, `jerusalemcross`, `pixels`, 4-sided `polyring` styles (those  employing structured meshes), and `sympixels`, and `false` for the remaining styles (those employing unstructured meshes).
