```
extended_gangoffour(P, C, pos=true)
```

Returns a single statespace system that maps 

  * `w1` reference or measurement noise
  * `w2` load disturbance

to

  * `z1` control error
  * `z2` control input

```
      z1          z2
      ▲  ┌─────┐  ▲      ┌─────┐
      │  │     │  │      │     │
w1──+─┴─►│  C  ├──┴───+─►│  P  ├─┐
    │    │     │      │  │     │ │
    │    └─────┘      │  └─────┘ │
    │                 w2         │
    └────────────────────────────┘
```

The returned system has the transfer-function matrix

$$
\begin{bmatrix}
I \\ C
\end{bmatrix} (I + PC)^{-1} \begin{bmatrix}
I & P
\end{bmatrix}
$$

or in code

```julia
# For SISO P
S  = G[1, 1]
PS = G[1, 2]
CS = G[2, 1]
T  = G[2, 2]

# For MIMO P
S  = G[1:P.ny,     1:P.nu]
PS = G[1:P.ny,     P.ny+1:end]
CS = G[P.ny+1:end, 1:P.ny]
T  = G[P.ny+1:end, P.ny+1:end] # Input complimentary sensitivity function
```

The gang of four can be plotted like so

```julia
Gcl = extended_gangoffour(G, C) # Form closed-loop system
bodeplot(Gcl, lab=["S" "PS" "CS" "T"], plotphase=false) |> display # Plot gang of four
```

Note, the last input of Gcl is the negative of the `PS` and `T` transfer functions from `gangoffour2`. To get a transfer matrix with the same sign as [`G_PS`](@ref) and [`input_comp_sensitivity`](@ref), call `extended_gangoffour(P, C, pos=false)`. See `glover_mcfarlane` from RobustAndOptimalControl.jl for an extended example. See also `ncfmargin` and `feedback_control` from RobustAndOptimalControl.jl.
