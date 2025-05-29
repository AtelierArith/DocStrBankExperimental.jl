```
assemble!(model, P, q, constraint(s); [settings, x0, y0, s0])
```

Assembles a `COSMO.Model` with a cost function defind by `P` and `q`, and a number of `constraints`.

The positive semidefinite matrix `P` and vector `q` are used to specify the cost function of the optimization problem:

```
min   1/2 x'Px + q'x
s.t.  Ax + b ∈ C
```

`constraints` is a `COSMO.Constraint` or an array of `COSMO.Constraint` objects that are used to describe the constraints on `x`.

---

The optional keyword argument `settings` can be used to pass custom solver settings:

```julia
custom_settings = COSMO.Settings(verbose = true);
assemble!(model, P, q, constraints, settings = custom_settings)
```

---

The optional keyword arguments `x0` and `y0` can be used to provide the solver with warm starting values for the primal variable `x` and the dual variable `y`.

```julia
x_0 = [1.0; 5.0; 3.0]
COSMO.assemble!(model, P, q, constraints, x0 = x_0)
```
