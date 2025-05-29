```
euler_approx(r::ContinuousResourceSharer, h::Float)
```

Transforms a continuous resource sharer `r` into a discrete resource sharer via Euler's method with step size `h`. If the dynamics of `r` is given by $\dot{u}(t) = f(u(t),p,t)$, then the dynamics of the new discrete system is given by the update rule $u_{n+1} = u_n + h f(u_n, p, t)$.
