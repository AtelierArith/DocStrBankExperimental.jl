```
layers(::Type{AbstractSatellite})
layers(x::AbstractSatellite)
```

Return the names of all layers available for the given sensor.

# Example

```julia
# Get all Available Layers for Landsat 8
landsat_layers = layers(Landsat8)

# Get all Available Layers for a Specific Scene
src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1")
available_layers = layers(src)
```
