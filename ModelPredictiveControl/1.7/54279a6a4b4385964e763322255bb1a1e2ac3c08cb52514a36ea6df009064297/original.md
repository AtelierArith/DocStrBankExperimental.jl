```
MultipleShooting()
```

Construct a direct multiple shooting [`TranscriptionMethod`](@ref).

The decision variable is (excluding $ϵ$):

$$
\mathbf{Z} = \begin{bmatrix} \mathbf{ΔU} \\ \mathbf{X̂_0} \end{bmatrix}
$$

thus it also includes the predicted states, expressed as deviation vectors from the operating point $\mathbf{x̂_{op}}$ (see [`augment_model`](@ref)):

$$
\mathbf{X̂_0} = \mathbf{X̂ - X̂_{op}} =            \begin{bmatrix} 
    \mathbf{x̂}_i(k+1)     - \mathbf{x̂_{op}}     \\ 
    \mathbf{x̂}_i(k+2)     - \mathbf{x̂_{op}}     \\ 
    \vdots                                      \\ 
    \mathbf{x̂}_i(k+H_p)   - \mathbf{x̂_{op}}     \end{bmatrix}
$$

where $\mathbf{x̂}_i(k+j)$ is the state prediction for time $k+j$, estimated by the observer at time $i=k$ or $i=k-1$ depending on its `direct` flag. Note that  $\mathbf{X̂_0 = X̂}$ if the operating point is zero, which is typically the case in practice for [`NonLinModel`](@ref). This transcription method is generally more efficient for large control horizon $H_c$, unstable or highly nonlinear plant models/constraints. 

Sparse optimizers like `OSQP` or `Ipopt` and sparse Jacobian computations are recommended for this transcription method.
