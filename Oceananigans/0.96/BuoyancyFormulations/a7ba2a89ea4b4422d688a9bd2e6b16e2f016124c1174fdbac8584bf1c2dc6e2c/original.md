```
BuoyancyForce(formulation; gravity_unit_vector=NegativeZDirection())
```

Construct a `buoyancy` given a buoyancy `model`. Optional keyword argument `gravity_unit_vector` can be used to specify the direction of gravity (default `NegativeZDirection()`). The buoyancy acceleration acts in the direction opposite to gravity.

# Example

```jldoctest
using Oceananigans

grid = RectilinearGrid(size=(1, 8, 8), extent=(1, 1, 1))

θ = 45 # degrees
g̃ = (0, -sind(θ), -cosd(θ))

buoyancy = BuoyancyForce(BuoyancyTracer(), gravity_unit_vector=g̃)

model = NonhydrostaticModel(; grid, buoyancy, tracers=:b)

# output

NonhydrostaticModel{CPU, RectilinearGrid}(time = 0 seconds, iteration = 0)
├── grid: 1×8×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×3×3 halo
├── timestepper: RungeKutta3TimeStepper
├── advection scheme: Centered(order=2)
├── tracers: b
├── closure: Nothing
├── buoyancy: BuoyancyTracer with ĝ = (0.0, -0.707107, -0.707107)
└── coriolis: Nothing
```
