Domain information for a ModelingToolkit.jl PDESystem. It can be used with the `+` operator to add initial and boundary conditions and coordinate transforms to a ModelingToolkit.jl ODESystem or Catalyst.jl ReactionSystem.

**NOTE**: The independent variable (usually time) must be first in the list of initial and boundary conditions.

  * `partial_derivative_funcs`: Function that returns spatial derivatives of the partially-independent variables, optionally performing a coordinate transformation first.

    Current function options in this package are:

      * `partialderivatives_δxyδlonlat`: Returns partial derivatives after transforming any variables named `lat` and `lon`

    from degrees to cartesian meters, assuming a spherical Earth.

    Other packages may implement additional functions. They are encouraged to use function names starting with `partialderivatives_`.

  * `grid_spacing`: The discretization intervals for the partial independent variables.
  * `icbc`: The sets of initial and/or boundary conditions.
  * `spatial_ref`: The spatial reference system for the domain.
  * `time_offset`: The time offset for the domain.
