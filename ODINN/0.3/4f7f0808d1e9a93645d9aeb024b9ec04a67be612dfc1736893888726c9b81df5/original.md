Struct to provide a dummy gradient. It does not have to be the true gradient. Mainly used to test that the optimization pileline works independenly of the gradient calculation.

`DummyAdjoint`

# Fields:

  * `grad::Function`: In-place function `f(du, u; kwargs)` that fills the first   argument `du` with the gradient values.
