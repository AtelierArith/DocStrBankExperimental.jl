```
initial(::Type{RandomInitialLayout}, N::T) where {T <: EcologicalNetworks.AbstractEcologicalNetwork}
```

Random disposition of nodes in a circle. This is a good starting point for any force-directed layout. The circle is scaled so that its radius is twice the square root of the network richness, which helps most layouts converge faster.
