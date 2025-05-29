```julia
SciMLBase.BVProblem{iip}(sys::AbstractODESystem, u0map, tspan,
                         parammap = DiffEqBase.NullParameters();
                         constraints = nothing, guesses = nothing,
                         version = nothing, tgrad = false,
                         jac = true, sparse = true,
                         simplify = false,
                         kwargs...) where {iip}
```

Create a boundary value problem from the [`ODESystem`](@ref). 

`u0map` is used to specify fixed initial values for the states. Every variable  must have either an initial guess supplied using `guesses` or a fixed initial  value specified using `u0map`.

Boundary value conditions are supplied to ODESystems in the form of a ConstraintsSystem. These equations  should specify values that state variables should take at specific points, as in `x(0.5) ~ 1`). More general constraints that  should hold over the entire solution, such as `x(t)^2 + y(t)^2`, should be  specified as one of the equations used to build the `ODESystem`.

If an ODESystem without `constraints` is specified, it will be treated as an initial value problem. 

```julia
    @parameters g t_c = 0.5
    @variables x(..) y(t) λ(t)
    eqs = [D(D(x(t))) ~ λ * x(t)
           D(D(y)) ~ λ * y - g
           x(t)^2 + y^2 ~ 1]
    cstr = [x(0.5) ~ 1]
    @mtkbuild pend = ODESystem(eqs, t; constraints = cstrs)

    tspan = (0.0, 1.5)
    u0map = [x(t) => 0.6, y => 0.8]
    parammap = [g => 1]
    guesses = [λ => 1]

    bvp = SciMLBase.BVProblem{true, SciMLBase.AutoSpecialize}(pend, u0map, tspan, parammap; guesses, check_length = false)
```

If the `ODESystem` has algebraic equations, like `x(t)^2 + y(t)^2`, the resulting  `BVProblem` must be solved using BVDAE solvers, such as Ascher.
