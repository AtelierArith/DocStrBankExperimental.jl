```
RefArea <: Area
```

A `RefArea` is an area representation with no additional constraints on energy/mass exchange.

# Fields

  * **`id`** is the name/identifier of the area.
  * **`name`** is the name of the area.
  * **`lon::Real`** is the longitudinal position of the area.
  * **`lat::Real`** is the latitudinal position of the area.
  * **`node::Availability`** is the `Availability` node routing different resources within an area.
