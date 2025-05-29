```
Wing(n_panels::Int;
     n_groups=n_panels,
     spanwise_distribution::PanelDistribution=LINEAR,
     spanwise_direction::PosVector=MVec3([0.0, 1.0, 0.0]),
     remove_nan::Bool=true)
```

Constructor for a [Wing](@ref) struct with default values that initializes the sections  and refined sections as empty arrays.

# Parameters

  * `n_panels::Int`: Number of panels in aerodynamic mesh
  * `n_groups::Int`: Number of panel groups in aerodynamic mesh
  * `spanwise_distribution`::PanelDistribution = LINEAR: [PanelDistribution](@ref)
  * `spanwise_direction::MVec3` = MVec3([0.0, 1.0, 0.0]): Wing span direction vector
  * `remove_nan::Bool`: Wether to remove the NaNs from interpolations or not
