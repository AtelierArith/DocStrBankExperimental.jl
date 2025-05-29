```
TimeCorrelationLogger(observableA::Function, observableB::Function,
                        TA::DataType, TB::DataType,
                        observable_length::Integer, n_correlation::Integer)
```

A time correlation logger.

Estimates statistical correlations of normalized form

$$
C(t)=\frac{\langle A_t\cdot B_0\rangle -\langle A\rangle\cdot \langle B\rangle}{\sqrt{\langle |A|^2\rangle\langle |B|^2\rangle}}
$$

or unnormalized form

$$
C(t)=\langle A_t\cdot B_0\rangle -\langle A \rangle\cdot \langle B\rangle
$$

These can be used to estimate statistical error, or to compute transport coefficients from Green-Kubo type formulas. *A* and *B* are observables, functions of the form `observable(sys::System, neighbors; n_threads::Integer)`. The return values of *A* and *B* can be of scalar or vector type (including `Vector{SVector{...}}`, like positions or velocities) and must implement `dot`.

`n_correlation` should typically be chosen so that `dt * n_correlation > t_corr`, where `dt` is the simulation timestep and `t_corr` is the decorrelation time for the considered system and observables. For the purpose of numerical stability, the logger internally records sums instead of running averages. The normalized and unnormalized form of the correlation function can be retrieved through `values(logger::TimeCorrelationLogger; normalize::Bool)`.

# Arguments

  * `observableA::Function`: the function corresponding to observable A.
  * `observableB::Function`: the function corresponding to observable B.
  * `TA::DataType`: the type returned by `observableA`, supporting `zero(TA)`.
  * `TB::DataType`: the type returned by `observableB`, supporting `zero(TB)`.
  * `observable_length::Integer`: the length of the observables if they are   vectors, or `1` if they are scalar-valued.
  * `n_correlation::Integer`: the length of the computed correlation vector.
