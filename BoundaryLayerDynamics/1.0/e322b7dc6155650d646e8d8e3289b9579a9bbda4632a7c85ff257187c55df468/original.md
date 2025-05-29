```
Model(resolution, domain, processes)
```

A `Model` provides a discretized representation of the dynamics of the specified `processes` within the specified `domain`.

It contains discretized state variables such as the velocity field that are initially set to zero, as well as all the information needed to efficiently compute the rate of change of these state variables. The required state variables are automatically determined from the specified processes.

# Arguments

  * `resolution::NTuple{3, Integer}`: The number of modes along the $x_1$ and $x_2$ direction, as well as the number of grid points along the $x_3$ direction. The first two values should be odd and will be reduced by one if they are even to ensure that the resolved wavenumbers are symmetric around zero.
  * `domain::Domain`: The simulated universum, represented with the [`Domain`](@ref) type.
  * `processes`: A list of the physical processes that govern the dynamical behavior of the state variables. For convenience, the list can be any iterable collection and can also be nested.

# Keywords

  * `comm::MPI.Comm`: The MPI communicator that the model will make use of. If not specified, `MPI.COMM_WORLD` is used. Note that specifying a different communicator is poorly tested currently and may lead to unexpected behavior.
