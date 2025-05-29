Minimal abstraction on top of symbolic tracing packages such as `Symbolics.jl` and `FastDifferentiation.jl` to make switching between the two easier.

In contrast to other abstraction layers, such as DifferentiationInterface.jl, this package does not only target automatic differentiation use-cases but also settings where tracing is performed merely to generate an efficient implementation of a user-defined function.
