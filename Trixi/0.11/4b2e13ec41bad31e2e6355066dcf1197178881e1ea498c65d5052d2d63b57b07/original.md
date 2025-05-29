```
jacobian_fd(semi::AbstractSemidiscretization;
            t0=zero(real(semi)),
            u0_ode=compute_coefficients(t0, semi))
```

Uses the right-hand side operator of the semidiscretization `semi` and simple second order finite difference to compute the Jacobian `J` of the semidiscretization `semi` at state `u0_ode`.
