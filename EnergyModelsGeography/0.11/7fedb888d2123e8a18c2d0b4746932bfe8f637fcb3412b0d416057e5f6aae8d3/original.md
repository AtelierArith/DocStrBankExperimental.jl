```
Transmission <: AbstractElement
```

A geographic corridor between two [`Area`](@ref)s where [`TransmissionMode`](@ref)s are used to transport resources.

# Fields

  * **`from::Area`** is the area resources are transported from.
  * **`to::Area`** is the area resources are transported to.
  * **`modes::Vector{<:Transmission}`** are the transmission modes that are available.
