```
unpack_ac_components(ac)
```

Helper function to unpack aircraft physical components.

!!! details "🔃 Inputs and Outputs"
    **Inputs:**

      * `ac::aircraft` : aircraft object to unpack

    **Outputs:**

      * `parg::AbstractArray{Float64}` : Geometry parameters
      * `options::Options` : aircraft configuration options
      * `fuse::Fuselage` : fuselage parameters
      * `fuse_tank::fuselage_tank` : fuel tank in fuselage parameters
      * `wing::Wing` : wing object
      * `htail::Tail` : horizontal stabilizer object
      * `vtail::Tail` : vertical stabilizer object
      * `landing_gear::LandingGear`: landing gear object

