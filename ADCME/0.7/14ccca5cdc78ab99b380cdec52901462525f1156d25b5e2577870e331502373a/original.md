```
ScipyOptimizerMinimize(sess::PyObject, opt::PyObject; kwargs...)
```

Minimizes a scalar Tensor. Variables subject to optimization are updated in-place at the end of optimization.

Note that this method does not just return a minimization Op, unlike `minimize`; instead it actually performs minimization by executing commands to control a Session https://www.tensorflow.org/api_docs/python/tf/contrib/opt/ScipyOptimizerInterface. See also [`ScipyOptimizerInterface`](@ref) and [`BFGS!`](@ref).

  * feed_dict: A feed dict to be passed to calls to session.run.
  * fetches: A list of Tensors to fetch and supply to loss_callback as positional arguments.
  * step_callback: A function to be called at each optimization step; arguments are the current values of all optimization variables packed into a single vector.
  * loss_callback: A function to be called every time the loss and gradients are computed, with evaluated fetches supplied as positional arguments.
  * run_kwargs: kwargs to pass to session.run.
