A solver strategy based on implicit-explicit (IMEX) time integration. See [here](https://docs.sciml.ai/DiffEqDocs/stable/types/split_ode_types/) for additional information.

kwargs:

  * stiff_sparse: Whether the stiff ODE function should use a sparse Jacobian.
  * stiff_tgrad: Whether the stiff ODE function should use an analytical time gradient.

Additional kwargs for ODEProblem constructor:

  * u0: initial condtions; if "nothing", default values will be used.
  * p: parameters; if "nothing", default values will be used.
  * name: name of the model.
