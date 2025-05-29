```
qnm_kerr(a, s, l, m, ω_guess; kwargs...)
```

Find the Kerr QNM using Leaver's method for the radial equation and the Cook-Zalutskiy approach for the angular sector. We use the unit $M = G = c = 1$.

# Arguments

  * `a`: Kerr parameter (dimensionless spin parameter, 0 ≤ |a| ≤ 1)
  * `s`: Spin weight of the field (±2 for gravitational perturbations, ±1 for electromagnetic perturbations, 0 for scalar perturbations)
  * `l`: Angular momentum quantum number (l ≥ |s|)
  * `m`: Azimuthal harmonic index (-l ≤ m ≤ l)
  * `ω_guess`: Initial guess for the QNM frequency

# Keyword Arguments

  * `n`: Overtone number (default: 0 for fundamental mode)
  * `A_guess`: Initial guess for the angular separation constant (default: nothing)
  * `poles`: Vector of known poles to subtract from the continued fraction (default: empty)
  * `l_max`: Maximum angular momentum for angular eigenvalue calculation (default: l + 20)
  * `cf_n_inv`: Number of inverse terms in the continued fraction (default: 0)
  * `cf_N_min`: Minimum number of terms in the continued fraction (default: 300)
  * `cf_N_max`: Maximum number of terms in the continued fraction (default: 100000)
  * `cf_tol`: Tolerance for continued fraction convergence (default: machine epsilon)
  * `nonlinear_algorithm`: Algorithm for solving the nonlinear eigenvalue problem (default: RobustMultiNewton with AutoFiniteDiff)
  * `angular_matrix_cache`: Pre-allocated matrix for angular eigenvalue calculation (default: nothing)
  * `kwargs...`: Additional keyword arguments passed to the nonlinear solver

# Returns

  * `Complex{TF}`: The complex QNM frequency $\omega$

# Examples

```julia
a = 0.7
s = 2
l = 2
m = 2
n = 0
ω = 0.532600243551018 - 0.08079287315500766im
l_max = 20

ω_pert = ω + rand(Complex{Float64}) / 1000

ωsol = qnm_kerr(a, s, l, m, ω_pert; n=n, l_max=l_max)
```

# Notes

  * The function uses a combination of Leaver's method for the radial equation and the Cook-Zalutskiy approach for the angular sector
  * The continued fraction method is used to solve the radial equation
  * The angular eigenvalue problem is solved using matrix eigenvalue methods
  * The function returns the complex frequency where the imaginary part is negative (damped modes)
