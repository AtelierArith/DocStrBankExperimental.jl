lines!(layer::Layer, args...)

Creates `Shapes` containing `GeometricObject`s of type `Layered.Line`, passing any trailing arguments to the constructor `Layered.Line.()`. Then appends the created `Shapes` to the given `Layer` `layer`.
