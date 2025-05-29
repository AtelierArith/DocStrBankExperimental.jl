```
Qd     = c2d(sys::StateSpace{Continuous}, Qc::Matrix, Ts;             opt=:o)
Qd, Rd = c2d(sys::StateSpace{Continuous}, Qc::Matrix, Rc::Matrix, Ts; opt=:o)
Qd     = c2d(sys::StateSpace{Discrete},   Qc::Matrix;                 opt=:o)
Qd, Rd = c2d(sys::StateSpace{Discrete},   Qc::Matrix, Rc::Matrix;     opt=:o)
```

Sample a continuous-time covariance or LQR cost matrix to fit the provided discrete-time system.

If `opt = :o` (default), the matrix is assumed to be a covariance matrix. The measurement covariance `R` may also be provided. If `opt = :c`, the matrix is instead assumed to be a cost matrix for an LQR problem.

!!! note
    Measurement covariance (here called `Rc`) is usually estimated in discrete time, and is in this case not dependent on the sample rate. Discretization of the measurement covariance only makes sense when a continuous-time controller has been designed and the closest corresponding discrete-time controller is desired.


The method used comes from theorem 5 in the reference below.

Ref: "Discrete-time Solutions to the Continuous-time Differential Lyapunov Equation With Applications to Kalman Filtering",  Patrik Axelsson and Fredrik Gustafsson

**On singular covariance matrices:** The traditional double integrator with covariance matrix `Qc = diagm([0,σ²])` warrants special consideration since it is rank-deficient, i.e., it indicates that there is a single source of randomness only, despite the presence of two state variables. If we assume that the noise is piecewise constant, we can use the input matrix ("Cholesky factor") of `Qc`, e.g., the noise of variance `σ²` enters like `N = [0, 1]` which is sampled using ZoH and becomes `Nd = [Ts^2 / 2; Ts]` which results in the covariance matrix `σ² * Nd * Nd'`. If we assume that the noise is a continuous-time white noise process, the discretized covariance matrix is full rank and can be computed by `c2d(sys::StateSpace{Continuous}, Qc, Ts)`. In some applications, a rank-1 approximation to this matrix is favored. In such situation, a good rank-1 approximation to this matrix is obtained by `σ² * Nd * Nd' ./ Ts`. This has the benefit of being both low rank, and produce covariance dynamics that are approximately invariant to the choice of sample interval. If the ZoH assumption is made, the covariance matrix is rank 1 but the covariance dynamics are not invariant to the choice of sample interval.`

# Example:

The following example designs a continuous-time LQR controller for a resonant system. This is simulated with OrdinaryDiffEq to allow the ODE integrator to also integrate the continuous-time LQR cost (the cost is added as an additional state variable). We then discretize both the system and the cost matrices and simulate the same thing. The discretization of an LQR contorller in this way is sometimes refered to as `lqrd`.

```julia
using ControlSystemsBase, LinearAlgebra, OrdinaryDiffEq, Test
sysc = DemoSystems.resonant()
x0 = ones(sysc.nx)
Qc = [1 0.01; 0.01 2] # Continuous-time cost matrix for the state
Rc = I(1)             # Continuous-time cost matrix for the input

L = lqr(sysc, Qc, Rc)
dynamics = function (xc, p, t)
    x = xc[1:sysc.nx]
    u = -L*x
    dx = sysc.A*x + sysc.B*u
    dc = dot(x, Qc, x) + dot(u, Rc, u)
    return [dx; dc]
end
prob = ODEProblem(dynamics, [x0; 0], (0.0, 10.0))
sol = solve(prob, Tsit5(), reltol=1e-8, abstol=1e-8)
cc = sol.u[end][end] # Continuous-time cost

# Discrete-time version
Ts = 0.01 
sysd = c2d(sysc, Ts)
Qd, Rd = c2d(sysd, Qc, Rc, opt=:c)
Ld = lqr(sysd, Qd, Rd)
sold = lsim(sysd, (x, t) -> -Ld*x, 0:Ts:10, x0 = x0)
function cost(x, u, Q, R)
    dot(x, Q, x) + dot(u, R, u)
end
cd = cost(sold.x, sold.u, Qd, Rd) # Discrete-time cost
@test cc ≈ cd rtol=0.01           # These should be similar
```
