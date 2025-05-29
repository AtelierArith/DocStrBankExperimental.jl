```
loadedcross(;s1::Vector{<:Real}, s2::Vector{<:Real}, L1::Real, L2::Real, w::Real, 
             ntri::Int, units::PSSFSSLength, kwargs...)
```

# Description:

Create a variable of type `RWGSheet` that contains the triangulation for a "loaded cross" type of geometry. The returned value has fields `s₁`, `s₂`, `β₁`, `β₂`, `ρ`, `e1`, `e2`, `fv`, `fe`,  and `fr` properly initialized.

The following (very poor) "ascii art" attempts to show the definitions of the geometrical parameters `L1`, `L2` and `w`. Note that the structure is supposed to be symmetrical wrt reflections about its horizontal and vertical centerlines, and wrt reflections through a line oriented at a 45 degree angle wrt the x-axis.

```
 ^                 ----------------
 |                 |  _________   |
 |                 |  |       |   |
 |                 |  |       |   |
 |                 |  |    -->|   |<--- W
 |                 |  |       |   |
 |                 |  |       |   |
 |     ------------   |       |   -------------
 |     |  |-----------|       |------------|  |
 |     |  |                                |  |
 L1    |  |                                |  |
 |     |  |                                |  |
 |     |  |                                |  |
 |     |  ------------          ------------  |
 |     |-----------   |        |  ------------|
 |                 |  |        |  |
 |                 |  |        |  |
 |                 |  |        |  |
 |                 |  |        |  |
 |                 |  |________|  |
 |                 |              |
 V                 ----------------

                   <---- L2 ------>
```

# Arguments:

All arguments are keyword arguments which can be entered in any order.

## Required arguments:

  * `s1` and `s2`:  2-vectors containing the unit cell lattice vectors.
  * `L1`,`L2`,`w`: Geometrical parameters as defined above.  Note that it is permissible  to specify `w ≥ L2/2` in which case a solid (i.e., singly-connected) cross will be   generated.  In that case the `L2` dimension will be used for the width of the cross pieces.
  * `units`:  Length units (`mm`, `cm`, `inch`, or `mil`)
  * `ntri`:  The desired total number of triangles.  This is a guide/request,  the actual number will likely be different.

## Optional arguments:

  * `orient::Real=0.0`:  Counterclockwise rotation angle in degrees used to locate the initial          vertex of the loaded cross.  The default is to locate the vertex on the          positive x-axis.
  * `class::Char='J'`  Specify the class, either `'J'` or `'M'`.. If `'J'`,  the unknowns are electric surface           currents, as used to model a wire or metallic patch-type FSS.  If `'M'`,  the unknowns are          magnetic surface currents, as used to model a slot or aperture in a perfectly conducting plane.
  * `dx::Real=0.0`, `dy::Real=0.0`:  These specify the offsets in the x and y directions applied to the entire           unit cell and its contents.  Length units are as specified in the `units` keyword.
  * `rot::Real=0.0`:  Counterclockwise rotation angle in degrees applied to the entire unit cell and its contents.           This rotation is applied prior to any offsets specified in `dx` and `dy`.
  * `Zsheet::Complex=0.0`:  The frequency-independent surface impedance of the FSS conductor in  units of [Ω].  May only be specified for a sheet of class `'J'`.  If `Zsheet` is specified, then  `sigma` (or `σ`) may not be specified.                          )
  * `sigma` or `σ`: DC, bulk conductivity [S/m].  Only allowed for sheets of class `'J'`.  Cannot be  simultaneously specified with `Zsheet`.  Is used with `Rq` by PSSFSS to calculate an effective  sheet surface impedance at each frequency, using the Gradient Model (Grujić 2022).
  * `Rq=0.0`: RMS surface roughness [m].  Only legal for class `'J'`. Only used if `sigma` (or `σ`) is   also specified.  In that case is is used along with `sigma` to calculate a frequency-dependent  sheet impedance using the Gradient Model.  The default value of 0 denotes a smooth surface.
  * `disttype::Symbol=:normal`: Probability distrubution type for surface roughness.  defaults to `:normal`.  The other legal value is `:rayleigh`.
  * `fufp::Bool`:  This keyword is not usually required.  `fufp` is mnemonic for "Find Unique Face Pairs".  If true, the code will search the  triangulation for classes of triangle pairs that are the equivalent in the toeplitz sense.  I.e., if triangle pairs (A,B) and (C,D) belong to the same equivalence class,  the six vertices in the pair (A,B) can be made to coincide  with those of pair (C,D) by a simple translation. If there are many such equivalent pairs,  a significant decrease in matrix fill time ensues by exploiting the equivalence.  The tradeoff is the time needed to identify them.  The default value is `true` for the `strip`, `diagstrip`,   `meander`, `manji`, `loadedcross`, `jerusalemcross`, `pixels`, 4-sided `polyring` styles (those  employing structured meshes), and `sympixels`, and `false` for the remaining styles (those employing unstructured meshes).
  * `structuredtri::Bool=true`: If true, use a structured mesh for the triangulation.  If false, the unstructured mesh generator that was standard up to PSSFSS version 1.2 will be used. A structured  mesh can be analyzed more efficiently, but the number of triangles created by the unstructured mesh generator is usually closer to `ntri` than the number for the structured mesh generator.
