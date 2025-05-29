Evaluate a morphism as a function.

If the morphism will be evaluated only once (possibly with vectorized inputs), then direct evaluation will be much faster than compiling (via `compile`) and evaluating a standard Julia function.

Compare with [`functor`](@ref).
