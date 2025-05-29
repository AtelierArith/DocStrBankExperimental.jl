beziers!(layer::Layer, args...)

Creates `Shapes` containing `GeometricObject`s of type `Layered.Bezier`, passing any trailing arguments to the constructor `Layered.Bezier.()`. Then appends the created `Shapes` to the given `Layer` `layer`.
