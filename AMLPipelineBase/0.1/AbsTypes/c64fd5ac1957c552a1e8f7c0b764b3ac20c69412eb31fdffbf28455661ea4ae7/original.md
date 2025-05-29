fit_transform!(mc::Machine, input::DataFrame, output::Vector)

Dynamic dispatch that calls in sequence `fit!` and `transform!` functions.
