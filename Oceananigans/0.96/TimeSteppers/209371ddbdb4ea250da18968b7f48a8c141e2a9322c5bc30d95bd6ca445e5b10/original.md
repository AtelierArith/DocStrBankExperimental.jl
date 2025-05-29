```
time_step!(model::AbstractModel{<:RungeKutta3TimeStepper}, Δt)
```

Step forward `model` one time step `Δt` with a 3rd-order Runge-Kutta method. The 3rd-order Runge-Kutta method takes three intermediate substep stages to achieve a single timestep. A pressure correction step is applied at each intermediate stage.
