---

The main constructor for compiling a `ParametricMCP` from

Positional arguments:

  * `f`: callable as `f(z, θ)` that maps a length `n` vector of decision variables `z` and a parameter vector `θ` of size `parameter_dimension` to an length `n` vector output.
  * `lower_bounds`: A length `n` vector of element-wise lower bounds on the decision variables `z`.
  * `upper_bounds`: A length `n` vector of element-wise upper bounds on the decision variables `z`.
  * `parameter_dimension`: the size of the parameter vector `θ` in `f`.

Keyword arguments:

  * `[backend]`: the backend (from `SymbolicTracingUtils`) to be used for compiling callbacks for `f` and its Jacobians needed by PATH. `SymbolicsBackend` (default) is slightly more flexible. `FastDifferentiationBackend` has reduced compilation times and reduced runtime in some cases.
  * `compute_sensitivities`: whether to compile the callbacks needed for sensitivity computation.
  * `[problem_size]`: the number of decision variables. If not provided and `lower_bounds` or `upper_bounds` are vectors, the problem size is inferred from the length of these vectors.

Note, this constructor uses symbolic tracing to compile the relevant low-level functions. Therefore, `f` must be implemented in a sufficiently generic way that supports symbolic evaluation. In cases where that is infeasible or impractical, you can still use the low-level constructor to generate a `ParametricMCP`. In general, however, the use of this convenience constructor is advised.
