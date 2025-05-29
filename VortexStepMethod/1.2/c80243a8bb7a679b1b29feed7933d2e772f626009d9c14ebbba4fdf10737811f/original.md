```
RamAirWing <: AbstractWing
```

A ram-air wing model that represents a curved parafoil with deformable aerodynamic surfaces.

## Core Features

  * Curved wing geometry derived from 3D mesh (.obj file)
  * Aerodynamic properties based on 2D airfoil data (.dat file)
  * Support for control inputs (twist angles and trailing edge deflections)
  * Inertial and geometric properties calculation

## Notable Fields

  * `n_panels::Int16`: Number of panels in aerodynamic mesh
  * `n_groups::Int16`: Number of control groups for distributed deformation
  * `mass::Float64`: Total wing mass in kg
  * `gamma_tip::Float64`: Angular extent from center to wing tip
  * `inertia_tensor::Matrix{Float64}`: Full 3x3 inertia tensor in the kite body frame
  * `T_cad_body::MVec3`: Translation vector from CAD frame to body frame
  * `R_cad_body::MMat3`: Rotation matrix from CAD frame to body frame
  * `radius::Float64`: Wing curvature radius
  * `theta_dist::Vector{Float64}`: Panel twist angle distribution
  * `delta_dist::Vector{Float64}`: Trailing edge deflection distribution

See constructor `RamAirWing(obj_path, dat_path; kwargs...)` for usage details.
