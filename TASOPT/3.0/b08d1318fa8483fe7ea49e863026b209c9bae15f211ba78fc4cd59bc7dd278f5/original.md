```
aircraft
```

A type representing a TASOPT aircraft model including, geometric, aerodynamic, propulsion system parameters. It is designed to hold information related to the aircraft's name, description, as well as different sets of parameters used for analysis and optimization.

Overloads Base.summary to print a summary of the `aircraft` model.

# Fields:

  * `name::String` : Aircraft name (eg: "Boeing 777")
  * `description::String` : A brief description of the aircraft
  * `options::TASOPT.Options` : Configuration options for the aircraft
  * `parg::AbstractArray{Float64}` : Geometry parameters
  * `parm::AbstractArray{Float64}` : Mission parameters
  * `para::AbstractArray{Float64}` : Aero parameters
  * `pare::AbstractArray{Float64}` : Engine parameters
  * `fuse_tank::fuselage_tank`: fuselage fuel tank object
  * `fuselage::Fuselage`: fuselage fuel tank object
  * `wing::Wing`: wing object
  * `htail::Tail`: horizontal tail object
  * `vtail::Tail`: vertical tail object
  * `engine::Engine`: engine object
  * `landing_gear::LandingGear`: landing gear object
  * `fuselage::Fuselage` : Fuselage layout, data, and parameters
  * `fuse_tank::fuselage_tank` : Fuselage tank data and parameters (when applicable)
  * `wing::Wing` : Wing data and parameters
  * `htail::Tail` : Horizontal tail data and parameters
  * `vtail::Tail` : Vertical tail data and parameters
  * `engine::Engine` : Engine models, data, and parameters

The indices for accessing specific data in the `par` arrays are defined in `/src/data_structs/index.inc`.  Refer to the sample input file (`/example/defaults/default_input.toml` and `read_input.jl`) for usage. Refer to the docs for a summary of the main `struct`s.
