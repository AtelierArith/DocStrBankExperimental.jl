arcs(f::Function, args...)

Creates shapes containing `GeometricObject`s of type `Layered.Arc`, storing any trailing arguments as dependencies, later to be passed as arguments to the given `Function` `f` that should return `GeometricObject`s of type `Layered.Arc` and will be evaluated when `solve!` is called on the shapes during the drawing process.
