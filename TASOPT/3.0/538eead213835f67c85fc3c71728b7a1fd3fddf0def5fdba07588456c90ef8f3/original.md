```
unpack_ac(ac, imission; ip = 0)
```

Helper function to unpack all aircraft parameters.

!!! details "🔃 Inputs and Outputs"
    **Inputs:**

      * `ac::aircraft` : aircraft object to unpack
      * `imission::Int64`: mission index
      * `ip::Int64`: mission point index (optional)

    **Outputs:**

      * `parg::AbstractArray{Float64}` : Geometry parameters
      * `parm::AbstractArray{Float64}` : Mission parameters
      * `para::AbstractArray{Float64}` : Aero parameters
      * `pare::AbstractArray{Float64}` : Engine parameters
      * `options::Options` : aircraft configuration options
      * `fuse::Fuselage` : fuselage parameters
      * `fuse_tank::fuselage_tank` : fuel tank in fuselage parameters
      * `wing::Wing` : wing object
      * `htail::Tail` : horizontal stabilizer object
      * `vtail::Tail` : vertical stabilizer object
      * `engine::Engine`: engine object
      * `landing_gear::LandingGear`: landing gear object

