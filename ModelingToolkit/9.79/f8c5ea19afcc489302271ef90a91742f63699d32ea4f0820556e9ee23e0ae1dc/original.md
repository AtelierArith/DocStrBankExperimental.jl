```
(; A, B, C, D), simplified_sys = linearize(sys, inputs, outputs;    t=0.0, op = Dict(), allow_input_derivatives = false, zero_dummy_der=false, kwargs...)
(; A, B, C, D)                 = linearize(simplified_sys, lin_fun; t=0.0, op = Dict(), allow_input_derivatives = false, zero_dummy_der=false)
```

Linearize `sys` between `inputs` and `outputs`, both vectors of variables. Return a NamedTuple with the matrices of a linear statespace representation on the form

$$
\begin{aligned}
ẋ &= Ax + Bu\\
y &= Cx + Du
\end{aligned}
$$

The first signature automatically calls [`linearization_function`](@ref) internally, while the second signature expects the outputs of [`linearization_function`](@ref) as input.

`op` denotes the operating point around which to linearize. If none is provided, the default values of `sys` are used.

If `allow_input_derivatives = false`, an error will be thrown if input derivatives ($u̇$) appear as inputs in the linearized equations. If input derivatives are allowed, the returned `B` matrix will be of double width, corresponding to the input `[u; u̇]`.

`zero_dummy_der` can be set to automatically set the operating point to zero for all dummy derivatives.

See also [`linearization_function`](@ref) which provides a lower-level interface, [`linearize_symbolic`](@ref) and [`ModelingToolkit.reorder_unknowns`](@ref).

See extended help for an example.

The implementation and notation follows that of ["Linear Analysis Approach for Modelica Models", Allain et al. 2009](https://ep.liu.se/ecp/043/075/ecp09430097.pdf)

# Extended help

This example builds the following feedback interconnection and linearizes it from the input of `F` to the output of `P`.

```

  r ┌─────┐       ┌─────┐     ┌─────┐
───►│     ├──────►│     │  u  │     │
    │  F  │       │  C  ├────►│  P  │ y
    └─────┘     ┌►│     │     │     ├─┬─►
                │ └─────┘     └─────┘ │
                │                     │
                └─────────────────────┘
```

```julia
using ModelingToolkit
using ModelingToolkit: t_nounits as t, D_nounits as D
function plant(; name)
    @variables x(t) = 1
    @variables u(t)=0 y(t)=0
    eqs = [D(x) ~ -x + u
           y ~ x]
    ODESystem(eqs, t; name = name)
end

function ref_filt(; name)
    @variables x(t)=0 y(t)=0
    @variables u(t)=0 [input = true]
    eqs = [D(x) ~ -2 * x + u
           y ~ x]
    ODESystem(eqs, t, name = name)
end

function controller(kp; name)
    @variables y(t)=0 r(t)=0 u(t)=0
    @parameters kp = kp
    eqs = [
        u ~ kp * (r - y),
    ]
    ODESystem(eqs, t; name = name)
end

@named f = ref_filt()
@named c = controller(1)
@named p = plant()

connections = [f.y ~ c.r # filtered reference to controller reference
               c.u ~ p.u # controller output to plant input
               p.y ~ c.y]

@named cl = ODESystem(connections, t, systems = [f, c, p])

lsys0, ssys = linearize(cl, [f.u], [p.x])
desired_order = [f.x, p.x]
lsys = ModelingToolkit.reorder_unknowns(lsys0, unknowns(ssys), desired_order)

@assert lsys.A == [-2 0; 1 -2]
@assert lsys.B == [1; 0;;]
@assert lsys.C == [0 1]
@assert lsys.D[] == 0

## Symbolic linearization
lsys_sym, _ = ModelingToolkit.linearize_symbolic(cl, [f.u], [p.x])

@assert substitute(lsys_sym.A, ModelingToolkit.defaults(cl)) == lsys.A
```
