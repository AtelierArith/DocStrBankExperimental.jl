boltzmann(eq::DiffusionEquation) -> DifferentialEquations.ODEFunction

Transform `eq` into an ordinary differential equation (ODE) defined in terms of the Boltzmann variable `o`.

Returns an ODE with independent variable `o` and two components, where the first is the solution itself and the second component is the `o`-derivative of the solution. The ODE is optimized for components stored in `StaticArrays.SVector`s.

See also: [`DifferentialEquations`](https://diffeq.sciml.ai/stable/), [`StaticArrays.SVector`](https://juliaarrays.github.io/StaticArrays.jl/stable/pages/api/#SVector-1)
