```
expansionentropy(ds::DynamicalSystem, sampler, isinside; kwargs...)
```

Calculate the expansion entropy[^Hunt2015] of `ds`, in the restraining region $S$ by estimating the slope (via linear regression) of the curve $\log E_{t0+T, t0}(f, S)$ versus $T$ (using [`linear_region`](@ref)). This is an approximation of the expansion entropy $H_0$, according to[^Hunt2015]. Return $T$,  $\log E$ and the calculated slope.

`sampler` is a 0-argument function that generates a random initial conditions of `ds` and `isinside` is a 1-argument function that given a state it returns true if the state is inside the restraining region. Typically `sampler, isinside` are the output of [`statespace_sampler`](@ref).

## Keyword arguments

  * `N = 1000`: Number of samples taken at each batch (same as $N$ of [^Hunt2015]).
  * `steps = 40`: The maximal steps for which the system will be run.
  * `batches = 100`: Number of batches to run the calculation, see below.
  * `Δt = 1`: Time evolution step size.
  * `J = nothing`: Jacobian function given to [`TangentDynamicalSystem`](@ref).

## Description

`N` samples are initialized and propagated forwards in time (along with their tangent space). At every time $t$ in `[t0+Δt, t0+2Δt, ..., t0+steps*Δt]` we calculate $H$:

$$
H[t] = \log E_{t0+T, t0}(f, S),
$$

with

$$
E_{t0+T, t0}(f, S) = \frac 1 N \sum_{i'} G(Df_{t0+t, t0}(x_i))
$$

(using same notation as [^Hunt2015]). In principle $E$ is the average largest possible growth ratio within the restraining region (sampled by the initial conditions). The summation is only over $x_i$ that stay inside the region $S$ defined by the boolean function `isinside`. This process is done by the `ChaosTools.expansionentropy_sample` function.

Then, this is repeated for `batches` amount of times, as recommended in[^Hunt2015]. From all these batches, the mean and std of $H$ is computed at every time point. This is done by the [`expansionentropy_batch`](@ref) function. When plotted versus $t$, these create the curves and error bars of e.g. Figs 2, 3 of [1].

This function `expansionentropy` simply returns the slope of the biggest linear region of the curve $H$ versus $t$, which approximates the expansion entropy $H_0$. It is therefore *recommended* to use [`expansionentropy_batch`](@ref) directly and evaluate the result yourself, as this step is known to be inaccurate for non-chaotic systems (where $H$ fluctuates strongly around 0).

[^Hunt2015]: Hunt & Ott, ‘Defining Chaos’, [Chaos 25.9 (2015)](https://doi.org/10/gdtkcf)
