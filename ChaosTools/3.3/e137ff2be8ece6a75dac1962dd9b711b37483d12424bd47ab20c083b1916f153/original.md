```
lyapunovspectrum(ds::DynamicalSystem, N, k = dimension(ds); kwargs...) -> λs
```

Calculate the spectrum of Lyapunov exponents [^Lyapunov1992] of `ds` by applying a QR-decomposition on the parallelepiped defined by the deviation vectors, in total for `N` evolution steps. Return the spectrum sorted from maximum to minimum. The third argument `k` is optional, and dictates how many lyapunov exponents to calculate (defaults to `dimension(ds)`).

See also [`lyapunov`](@ref), [`local_growth_rates`](@ref).

**Note:** This function simply initializes a [`TangentDynamicalSystem`](@ref) and calls the method below. This means that the automatic Jacobian is used by default. Initialize manually a [`TangentDynamicalSystem`](@ref) if you have a hand-coded Jacobian.

## Keyword arguments

  * `u0 = current_state(ds)`: State to start from.
  * `Ttr = 0`: Extra transient time to evolve the system before application of the algorithm. Should be `Int` for discrete systems. Both the system and the deviation vectors are evolved for this time.
  * `Δt = 1`: Time of individual evolutions between successive orthonormalization steps. For continuous systems this is approximate.
  * `show_progress = false`: Display a progress bar of the process.

## Description

The method we employ is "H2" of [^Geist1990], originally stated in [^Benettin1980], and explained in educational form in [^DatserisParlitz2022].

The deviation vectors defining a `D`-dimensional parallelepiped in tangent space are evolved using the tangent dynamics of the system (see [`TangentDynamicalSystem`](@ref)). A QR-decomposition at each step yields the local growth rate for each dimension of the parallelepiped. At each step the parallelepiped is re-normalized to be orthonormal. The growth rates are then averaged over `N` successive steps, yielding the lyapunov exponent spectrum.

[^Lyapunov1992]: A. M. Lyapunov, *The General Problem of the Stability of Motion*, Taylor & Francis (1992)

[^Geist1990]: K. Geist *et al.*, Progr. Theor. Phys. **83**, pp 875 (1990)

[^Benettin1980]: G. Benettin *et al.*, Meccanica **15**, pp 9-20 & 21-30 (1980)

[^DatserisParlitz2022]: Datseris & Parlitz 2022, *Nonlinear Dynamics: A Concise Introduction Interlaced with Code*, [Springer Nature, Undergrad. Lect. Notes In Physics](https://doi.org/10.1007/978-3-030-91032-7)
