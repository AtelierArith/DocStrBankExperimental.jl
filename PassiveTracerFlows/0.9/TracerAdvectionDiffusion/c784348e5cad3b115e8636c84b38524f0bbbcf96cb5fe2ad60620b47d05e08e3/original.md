```
Problem(dev::Device=CPU(), advecting_flow; parameters...)
```

Construct a constant diffusivity problem with steady or time-varying `advecting_flow` on device `dev`. The default device is the `CPU()`, to use the `GPU` pass the argument to the function The dimensionality of the problem is inferred from the type of `advecting_flow` provided:

  * `advecting_flow::OneDAdvectingFlow` for 1D advection-diffusion problem,
  * `advecting_flow::TwoDAdvectingFlow` for 2D advection-diffusion problem,
  * `advecting_flow::ThreeDAdvectingFlow` for 3D advection-diffusion problem.
