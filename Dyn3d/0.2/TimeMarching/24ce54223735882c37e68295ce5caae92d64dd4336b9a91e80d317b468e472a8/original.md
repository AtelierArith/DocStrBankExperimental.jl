```
HERKBody is a half-explicit Runge-Kutta solver based on the
constrained body model in paper of V.Brasey and E.Hairer.
The following ODE system is being solved:
   | dq/dt = v                     |
   | M(q)*dv/dt = f(q,v) - GT(q)*λ |
   | 0 = G(q)*v + gti(q)           |
, where GT is similar to the transpose of G.

Note that this is a index-2 system with two variables q and u.
Here we denote for a body chain, v stands for body velocity
and vJ stands for joint velocity. Similarly for q and qJ. λ is the
constraint on q to be satisfied.

Specificlly for the dynamics problem, we choose to solve for qJ and v.
The system of equation is actually:
   | dqJ/dt = vJ                              |
   | M(qJ)*dv/dt = f(qJ,v,vJ) - GT(qJ)*lambda |
   | 0 = G(qJ)*v + gti(qJ)                    |
So we need a step to calculate v from vJ solved. The motion constraint
(prescribed active motion) is according to joint, not body.

Here we write the system of equations in a general form:
[A B₁ᵀ] * [v] = [r₁]
[B₂ 0 ]   [λ]   [r₂]
so A = M(qJ), B₁ᵀ = GT(qJ), B₂ = G(qJ), r₁ = f(qJ,v,vJ), r₂ = -gti(qJ)
the equation of dqJ/dt = vJ gets updated in HERK.
```
