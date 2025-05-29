lines!(f::Function, layer::Layer, args...)

Creates multiple shapes containing `GeometricObject`s of type `Layered.Line`, storing any trailing arguments as dependencies, later to be passed as arguments to the given `Function` `f` that should return the `GeometricObject`s of type `Layered.Line` and will be evaluated when `solve!` is called on the shapes during the drawing process. This function then appends the created shapes to the given `Layer` `layer`.
