A system for composing together other systems using the [`couple`](@ref) function.

  * `systems`: Model components to be composed together
  * `domaininfo`: Initial and boundary conditions and other domain information
  * `pdefunctions`: A vector of functions where each function takes as an argument the resulting PDESystem after DomainInfo is added to this system, and returns a transformed PDESystem.

  * `ops`: A vector of operators to run during simulations.

  * `callbacks`: A vector of callbacks to run during simulations.
  * `init_callbacks`: Objects `x` with an `init_callback(x, Simulator)::DECallback` method.

Things that can be added to a `CoupledSystem`:

  * `ModelingToolkit.ODESystem`s. If the ODESystem has a field in the metadata called `:coupletype` (e.g. `ModelingToolkit.get_metadata(sys)[:coupletype]` returns a struct type with a single field called `sys`) then that type will be used to check for methods of `EarthSciMLBase.couple` that use that type.
  * [`Operator`](@ref)s
  * [`DomainInfo`](@ref)s
  * [Callbacks](https://docs.sciml.ai/DiffEqDocs/stable/features/callback_functions/)
  * Types `X` that implement a `EarthSciMLBase.init_callback(::X, ::CoupledSystem, sys_mtk, ::DomainInfo, ::MapAlgorithm)::DECallback` method
  * Other `CoupledSystem`s
  * Types `X` that implement a `EarthSciMLBase.couple2(::X, ::CoupledSystem)` or `EarthSciMLBase.couple2(::CoupledSystem, ::X)` method.
  * `Tuple`s or `AbstractVector`s of any of the things above.
