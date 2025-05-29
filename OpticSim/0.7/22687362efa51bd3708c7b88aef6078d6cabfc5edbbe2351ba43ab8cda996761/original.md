```
ParaxialLens{T} <: Surface{T}
```

`surfacenormal` is the **output** direction of the lens. Paraxial lens cannot act as the interface between two materials, hence only a single outside material is specified, by default Air.

Create with the following functions

```julia
ParaxialLensEllipse(focaldistance, halfsizeu, halfsizev, surfacenormal, centrepoint; rotationvec = [0.0, 1.0, 0.0], outsidematerial = AGFFileReader.Air, decenteruv = (0.0, 0.0))
ParaxialLensRect(focaldistance, halfsizeu, halfsizev, surfacenormal, centrepoint; rotationvec = [0.0, 1.0, 0.0], outsidematerial = AGFFileReader.Air, decenteruv = (0.0, 0.0))
ParaxialLensHex(focaldistance, side_length, surfacenormal, centrepoint; rotationvec = [0.0, 1.0, 0.0], outsidematerial = AGFFileReader.Air, decenteruv = (0.0, 0.0))
ParaxialLensConvexPoly(focaldistance, local_frame, local_polygon_points, local_center_point; outsidematerial = AGFFileReader.Air)
```
