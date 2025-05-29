```
FresnelInterface{T} <: OpticalInterface{T}
```

Interface between two materials with behavior defined according to the [Fresnel equations](https://en.wikipedia.org/wiki/Fresnel_equations), with a specified reflectance and transmission. Assumes unpolarized light.

```julia
FresnelInterface{T}(insidematerial, outsidematerial; reflectance = 0, transmission = 1, interfacemode = ReflectOrTransmit)
```

The interfacemode can be used to trace rays deterministically. Valid values are defined in the InterfaceMode enum. Reflect means that all values are reflected, Transmit means that all values are transmitted. ReflectOrTransmit will randomly reflect and transmit rays with the distribution given by the reflection and transmission arguments. This is also the default. In all cases the power recorded with the ray is correctly updated. This can be used to fake sequential raytracing. For example a beamsplitter surface may be set to either Reflect or Transmit to switch between the two outgoing ray paths.
