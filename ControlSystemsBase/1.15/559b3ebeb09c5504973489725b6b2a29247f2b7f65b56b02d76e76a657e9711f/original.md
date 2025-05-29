```
lqr(sys, Q, R)
lqr(Continuous, A, B, Q, R, args...; kwargs...)
lqr(Discrete, A, B, Q, R, args...; kwargs...)
```

Calculate the optimal gain matrix `K` for the state-feedback law `u = -K*x` that minimizes the cost function:

J = integral(x'Qx + u'Ru, 0, inf) for the continuous-time model `dx = Ax + Bu`. J = sum(x'Qx + u'Ru, 0, inf) for the discrete-time model `x[k+1] = Ax[k] + Bu[k]`.

Solve the LQR problem for state-space system `sys`. Works for both discrete and continuous time systems.

The `args...; kwargs...` are sent to the Riccati solver, allowing specification of cross-covariance etc. See `?MatrixEquations.arec / ared` for more help.

To obtain also the solution to the Riccati equation and the eigenvalues of the closed-loop system as well, call `ControlSystemsBase.MatrixEquations.arec / ared` instead (note the different order of the arguments to these functions).

To obtain a discrete-time approximation to a continuous-time LQR problem, the function [`c2d`](@ref) can be used to obtain corresponding discrete-time cost matrices.

# Examples

Continuous time

```julia
using LinearAlgebra # For identity matrix I
using Plots
A = [0 1; 0 0]
B = [0; 1]
C = [1 0]
sys = ss(A,B,C,0)
Q = I
R = I
L = lqr(sys,Q,R) # lqr(Continuous,A,B,Q,R) can also be used

u(x,t) = -L*x # Form control law,
t=0:0.1:5
x0 = [1,0]
y, t, x, uout = lsim(sys,u,t,x0=x0)
plot(t,x', lab=["Position" "Velocity"], xlabel="Time [s]")
```

Discrete time

```julia
using LinearAlgebra # For identity matrix I
using Plots
Ts = 0.1
A = [1 Ts; 0 1]
B = [0;1]
C = [1 0]
sys = ss(A, B, C, 0, Ts)
Q = I
R = I
L = lqr(Discrete, A,B,Q,R) # lqr(sys,Q,R) can also be used

u(x,t) = -L*x # Form control law,
t=0:Ts:5
x0 = [1,0]
y, t, x, uout = lsim(sys,u,t,x0=x0)
plot(t,x', lab=["Position"  "Velocity"], xlabel="Time [s]")
```

# FAQ

This function requires

  * `Q` must be positive semi-definite
  * `R` must be positive definite
  * The pair `(Q,A)` must not have any unobservable modes on the imaginary axis (cont) / unit circle (disc), e.g., there must not be any integrating modes that are not penalized by `Q`. if this condition does not hold, you may get the error "The Hamiltonian matrix is not dichotomic".
