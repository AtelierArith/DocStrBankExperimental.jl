```
City
```

Store a city made of [`Junction`](@ref)s and [`Street`](@ref)s, along with additional instance parameters.

# Fields

  * `total_duration::Int`: total time allotted for the car itineraries (in seconds)
  * `nb_cars::Int`: number of cars in the fleet
  * `starting_junction::Int`: junction at which all the cars are located initially
  * `junctions::Vector{Junction}`: list of junctions
  * `streets::Vector{Street}`: list of streets
