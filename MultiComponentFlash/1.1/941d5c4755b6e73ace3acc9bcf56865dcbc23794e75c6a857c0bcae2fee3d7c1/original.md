```
flash_2ph(eos, c, [K], [V]; <keyword arguments>)
```

Perform two-phase flash with a given EOS under a set of specific conditions. Returns vapor fraction. Modifies K in-place.

Given a mixture with pressure, temperature and mole fractions, this routine performs a vapor-liquid equilibrium calculation after a stability test.

Two outcomes are possible:

1. A single-phase condition prevails (returned vapor fraction is `NaN`) and a single phase (liquid or vapor) is stable.
2. A two-phase condition is possible. The routine produces K-values and vapor fraction so that the following holds:

    1. Isofugacity constraint for all components ($f_{li} = f_{vi}$)
    2. Molar balance for all components ($(1-V) x_i - V y_i - z_i$)
    3. Unity condition ($\sum_i (x_i - y_i) = 0$)

# Arguments

  * `eos`: the equation-of-state to be used for the flash
  * `c`: conditions to flash the mixture at on the form `(p = 10e5, T = 303.15, z = [0.5, 0.3, 0.2])`
  * `K`: optionally a buffer of length `number_of_components(eos)` used to hold K-values. Modified in-place.
  * `V`: optionally the initial guess for V. If this value is not `NaN`, the stability check will be skipped.

# Keyword arguments

  * `method = SSIFlash()`: Flash method to use. Can be `SSIFlash()`, `NewtonFlash()` or `SSINewtonFlash()`.
  * `tolerance = 1e-8`: Tolerance for the convergence criterion. Relative to $\|1-R_i\|_\infty$ where $R_i = f_{il}/f_{iv}$
  * `maxiter = 20000`: Maximum nubmer of iterations for both stability tests and the main flash.
  * `verbose = false`: Emit extra information during solve.
  * `extra_out = false`: Return `(V, K, conv)` where `conv` contains iterations and oncergence status instead of just `V`.
  * `check = true`: Output warning (if not converged) and errors (if flash failed)
  * `z_min`: Minimum composition (enforced if provided)

See also: [`flash_2ph!`](@ref), [`single_phase_label`](@ref)
