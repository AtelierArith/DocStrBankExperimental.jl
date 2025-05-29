paths!(layer::Layer, args...)

Creates `Shapes` containing `GeometricObject`s of type `Layered.Path`, passing any trailing arguments to the constructor `Layered.Path.()`. Then appends the created `Shapes` to the given `Layer` `layer`.
