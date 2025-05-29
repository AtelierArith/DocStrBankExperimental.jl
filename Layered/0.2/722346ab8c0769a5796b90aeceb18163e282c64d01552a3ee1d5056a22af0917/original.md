rect!(f::Function, layer::Layer, args...)

Creates a shape containing a `GeometricObject` of type `Layered.Rect`, storing any trailing arguments as dependencies, later to be passed as arguments to the given `Function` `f` that should return a `GeometricObject` of type `Layered.Rect` and will be evaluated when `solve!` is called on the shape during the drawing process. This function then appends the created shape to the given `Layer` `layer`.
