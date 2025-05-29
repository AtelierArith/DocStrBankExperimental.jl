```
euler_approx(m::ContinuousMachine, h::Float)
```

Transforms a continuous machine `m` into a discrete machine via Euler's method with step size `h`. If the dynamics of `m` is given by $\dot{u}(t) = f(u(t),x(t),p,t)$, then the dynamics of the new discrete system is given by the update rule $u_{n+1} = u_n + h f(u_n, x_n, p, t)$.
