```
extended_controller(l::LQGProblem, L = lqr(l), K = kalman(l); z = nothing)
```

Returns a statespace system representing the controller that is obtained when state-feedback `u = L(xᵣ-x̂)` is combined with a Kalman filter with gain `K` that produces state estimates x̂. The controller is an instance of `ExtendedStateSpace` where `C2 = -L, D21 = L` and `B2 = K`.

The returned system has *inputs* `[xᵣ; y]` and outputs the control signal `u`. If a reference model `R` is used to generate state references `xᵣ`, the controller from `(ry, y) -> u`  where `ry - y = e` is given by

```julia
Ce = extended_controller(l)
Ce = named_ss(ss(Ce); x = :xC, y = :u, u = [R.y; :y^l.ny]) # Name the inputs of Ce the same as the outputs of `R`.
connect([R, Ce]; u1 = R.y, y1 = R.y, w1 = [R.u; :y^l.ny], z1=[:u])
```

Since the negative part of the feedback is built into the returned system, we have

```julia
C = observer_controller(l)
Ce = extended_controller(l)
system_mapping(Ce) == -C
```

Please note, without the reference pre-filter, the DC gain from references to controlled outputs may not be identity. If a vector of output indices is provided through the keyword argument `z`, the closed-loop system from state reference `xᵣ` to outputs `z` is returned as a second return argument. The inverse of the DC-gain of this closed-loop system may be useful to compensate for the DC-gain of the controller.
