```
Camera(pixel_area)
```

Struct to hold all relevant matrices and additional parameters, to let backends apply camera based transformations.

## Fields

  * `pixel_space::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float32, 16}}`: projection used to convert pixel to device units

  * `view::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float32, 16}}`: View matrix is usually used to rotate, scale and translate the scene

  * `projection::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float32, 16}}`: Projection matrix is used for any perspective transformation

  * `projectionview::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float32, 16}}`: just projection * view

  * `resolution::Observables.Observable{GeometryBasics.Vec{2, Float32}}`: resolution of the canvas this camera draws to

  * `lookat::Observables.Observable{GeometryBasics.Vec{3, Float32}}`: Focal point of the camera, used for e.g. camera synchronized light direction.

  * `eyeposition::Observables.Observable{GeometryBasics.Vec{3, Float32}}`: Eye position of the camera, used for e.g. ray tracing.

  * `steering_nodes::Vector{Observables.ObserverFunction}`: To make camera interactive, steering observables are connected to the different matrices. We need to keep track of them, so, that we can connect and disconnect them.

  * `calculated_values::Dict{Symbol, Observables.Observable}`
