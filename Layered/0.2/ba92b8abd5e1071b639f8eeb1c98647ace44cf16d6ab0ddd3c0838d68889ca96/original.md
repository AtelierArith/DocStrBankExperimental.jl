polygons!(layer::Layer, args...)

Creates `Shapes` containing `GeometricObject`s of type `Layered.Polygon`, passing any trailing arguments to the constructor `Layered.Polygon.()`. Then appends the created `Shapes` to the given `Layer` `layer`.
