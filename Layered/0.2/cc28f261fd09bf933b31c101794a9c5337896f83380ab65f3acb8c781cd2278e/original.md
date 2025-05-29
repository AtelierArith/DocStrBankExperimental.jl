points!(layer::Layer, args...)

Creates `Shapes` containing `GeometricObject`s of type `Layered.Point`, passing any trailing arguments to the constructor `Layered.Point.()`. Then appends the created `Shapes` to the given `Layer` `layer`.
