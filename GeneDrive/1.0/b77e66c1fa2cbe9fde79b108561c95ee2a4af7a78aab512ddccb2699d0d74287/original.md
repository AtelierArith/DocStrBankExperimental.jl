```
mutable struct Node
    name::Symbol
    organisms::DataStructures.OrderedDict{Type{<:Species}, Organism}
    temperature::Temperature
    location::Tuple{Float64,Float64}
end
```

Data for a single spatial node.

# Arguments

  * `name::Symbol`: Name of node, usually location-relevant.
  * `organisms::DataStructures.OrderedDict{Type{<:Species}, Organism}`: Dictionary containing data for all species inhabiting node.
  * `temperature::Temperature`: Climatic specification for temperature.
  * `location::Tuple{Float64,Float64}`: Geographic location denoted by coordinates.
