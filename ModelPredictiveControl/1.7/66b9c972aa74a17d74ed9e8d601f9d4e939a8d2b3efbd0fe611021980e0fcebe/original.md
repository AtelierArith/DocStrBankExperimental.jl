```
LinModel(sys::StateSpace[, Ts]; i_u=1:size(sys,2), i_d=Int[])
```

Construct a linear model from state-space model `sys` with sampling time `Ts` in second.

The system `sys` can be continuous or discrete-time (`Ts` can be omitted for the latter). For continuous dynamics, its state-space equations are (discrete case in Extended Help):

$$
\begin{aligned}
    \mathbf{ẋ}(t) &= \mathbf{A x}(t) + \mathbf{B z}(t) \\
    \mathbf{y}(t) &= \mathbf{C x}(t) + \mathbf{D z}(t)
\end{aligned}
$$

with the state $\mathbf{x}$ and output $\mathbf{y}$ vectors. The $\mathbf{z}$ vector  comprises the manipulated inputs $\mathbf{u}$ and measured disturbances $\mathbf{d}$,  in any order. `i_u` provides the indices of $\mathbf{z}$ that are manipulated, and `i_d`,  the measured disturbances. The constructor automatically discretizes continuous systems, resamples discrete ones if `Ts ≠ sys.Ts`, computes a new balancing and minimal state-space realization, and separates the $\mathbf{z}$ terms in two parts (details in Extended Help).  The rest of the documentation assumes discrete models since all systems end up in this form.

See also [`ss`](@extref ControlSystemsBase.ss)

# Examples

```jldoctest
julia> model1 = LinModel(ss(-0.1, 1.0, 1.0, 0), 2.0) # continuous-time StateSpace
LinModel with a sample time Ts = 2.0 s and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d

julia> model2 = LinModel(ss(0.4, 0.2, 0.3, 0, 0.1)) # discrete-time StateSpace
LinModel with a sample time Ts = 0.1 s and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    The state-space equations are similar if `sys` is discrete-time:

    $$
    \begin{aligned}
        \mathbf{x}(k+1) &=  \mathbf{A x}(k) + \mathbf{B z}(k) \\
        \mathbf{y}(k)   &=  \mathbf{C x}(k) + \mathbf{D z}(k)
    \end{aligned}
    $$

    Continuous dynamics are internally discretized using [`c2d`](@extref ControlSystemsBase.c2d) and `:zoh` for manipulated inputs, and `:tustin`, for measured disturbances. Lastly, if `sys` is discrete and the provided argument `Ts ≠ sys.Ts`, the system is resampled by using the aforementioned discretization methods.

    Note that the constructor transforms the system to its minimal and balancing realization using [`minreal`](@extref ControlSystemsBase.minreal) for controllability/observability. As a consequence, the final state-space representation will be presumably different from the one provided in `sys`. It is also converted into a more practical form ($\mathbf{D_u=0}$ because of the zero-order hold):

    $$
    \begin{aligned}
        \mathbf{x}(k+1) &=  \mathbf{A x}(k) + \mathbf{B_u u}(k) + \mathbf{B_d d}(k) \\
        \mathbf{y}(k)   &=  \mathbf{C x}(k) + \mathbf{D_d d}(k)
    \end{aligned}
    $$

    Use the syntax [`LinModel{NT}(A, Bu, C, Bd, Dd, Ts)`](@ref) to force a specific state-space representation.

