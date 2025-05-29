```
modeshape(model::Bar, kn, x, bc = :CC)
modeshape(model::Rod, kn, x, bc = :CC)
modeshape(model::Strings, kn, x, bc = :CC)
modeshape(model::Beam, kn, x, bc = :SS)
```

Computes the mass-normalized mode shapes of a longitudinal or torsional bar

**Inputs**

  * `model`: Structure containing the bar data
  * `kn`: Array of modal wavenumbers
  * `x`: Coordinates of calculation points of the mode shapes
  * `bc`: Boundary conditions

      * For all OneDStructure

          * `:CC`: Clamped - Clamped
          * `:CF`: Clamped - Free
          * `:FF`: Free - Free
      * For beams

          * `:SS`: Simply Supported - Simply Supported
          * `:SC`: Simply Supported - Clamped
          * `:SF`: Simply Supported - Free

**Output**

  * `ϕ`: Mass-normalized mode shapes
