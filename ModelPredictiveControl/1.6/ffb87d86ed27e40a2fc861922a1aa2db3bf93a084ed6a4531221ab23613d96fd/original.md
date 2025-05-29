```
SingleShooting()
```

Construct a direct single shooting [`TranscriptionMethod`](@ref).

The decision variable in the optimization problem is (excluding the slack $ϵ$):

$$
\mathbf{Z} = \mathbf{ΔU} =          \begin{bmatrix} 
    \mathbf{Δu}(k+0)                \\ 
    \mathbf{Δu}(k+1)                \\ 
    \vdots                          \\ 
    \mathbf{Δu}(k+H_c-1)            \end{bmatrix}
$$

This method is generally more efficient for small control horizon $H_c$, stable and mildly nonlinear plant model/constraints.
