```
fit(ICA, X, k; ...)
```

Perform ICA over the data set given in `X`.

**Parameters:** -`X`: The data matrix, of size $(m, n)$. Each row corresponds to a mixed signal, while each column corresponds to an observation (*e.g* all signal value at a particular time step). -`k`: The number of independent components to recover.

**Keyword Arguments:**

  * `alg`: The choice of algorithm (*default* `:fastica`)
  * `fun`: The approx neg-entropy functor (*default* [`Tanh`](@ref))
  * `do_whiten`: Whether to perform pre-whitening (*default* `true`)
  * `maxiter`: Maximum number of iterations (*default* `100`)
  * `tol`: Tolerable change of $W$ at convergence (*default* `1.0e-6`)
  * `mean`: The mean vector, which can be either of:

      * `0`: the input data has already been centralized
      * `nothing`: this function will compute the mean (*default*)
      * a pre-computed mean vector
  * `winit`: Initial guess of $W$, which should be either of:

      * empty matrix: the function will perform random initialization (*default*)
      * a matrix of size $(k, k)$ (when `do_whiten`)
      * a matrix of size $(m, k)$ (when `!do_whiten`)

Returns the resultant ICA model, an instance of type [`ICA`](@ref).

**Note:** If `do_whiten` is `true`, the return `W` satisfies $\mathbf{W}^T \mathbf{C} \mathbf{W} = \mathbf{I}$, otherwise $W$ is orthonormal, *i.e* $\mathbf{W}^T \mathbf{W} = \mathbf{I}$.
