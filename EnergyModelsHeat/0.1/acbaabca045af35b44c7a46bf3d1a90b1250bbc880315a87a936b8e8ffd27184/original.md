```
DHPipe
```

A DH pipe between two nodes.

# Fields

  * **`id`** is the name/identifier of the link.
  * **`from::Node`** is the node from which there is flow into the link.
  * **`to::Node`** is the node to which there is flow out of the link.
  * **`cap::TimeProfile`** is the heat transport capacity of the pipe
  * **`pipe_length::Float64`** is the pipe length in meters
  * **`pipe_loss_factor::Float64`** is the heat loss factor in [W m⁻¹ K⁻¹].
  * **`t_ground::TimeProfile`** is the ground temperature in °C.
  * **`resource_heat::ResourceHeat` is the resource used by DHPipe
  * **`formulation::Formulation`** is the used formulation of links. The field `formulation` is conditional through usage of a constructor.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
