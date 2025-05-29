```julia
abstract type AbstractNLS end 
```

Defines an abstract non-linear least squares problem (NLS). In our context such problem is essentially a differentiable function $\mathbf{r}$:

$$
\mathbf{r}: \theta\in\mathbb{R}^{n_θ}\mapsto \mathbf{r}(\mathbf{\theta})\in\mathbb{R}^{n_S}
$$

where:

  * $\mathbf{r}(\mathbf{θ})∈\mathbb{R}^{n_S}$ is the residue vector,
  * $\mathbf{θ}∈\mathbb{R}^{n_θ}$ is the parameter vector to be optimized

The objective function to minimize is:

$$
f(θ)=\frac{1}{2}\| \mathbf{r}(θ) \|^2
$$

The classical approach uses a linear approximation of $\mathbf{r}$:

$$
\mathbf{r}(\mathbf{θ}+δ\mathbf{θ})\approx \mathbf{r}(\mathbf{θ}) + \mathbf{J}(\mathbf{θ})\cdot δ\mathbf{θ}
$$

where $\mathbf{J}$ is the Jacobian:

$$
\mathbf{J}_{i,j}=\partial_j r^i(\mathbf{θ}),\ i\in[1,n_S],\ j\in[1,n_θ]
$$

This leads to

$$
f(\mathbf{θ}+δ\mathbf{θ})\approx f(\mathbf{θ}) + \langle \nabla f, δ\mathbf{θ} \rangle + \frac{1}{2}  \langle \nabla^2 f \cdot δ\mathbf{θ},  δ\mathbf{θ} \rangle
$$

Where the gradient $\nabla f$ is $\mathbf{J}^t \mathbf{r}$ and the (approximate) Hessian $\nabla^2 f$ is $\mathbf{J}^t \mathbf{J}$.

To implement such model, you must define the following functions:

  * [`parameter_size`](@ref) : returns $n_θ$
  * [`residue_size`](@ref) : returns $n_S$
  * [`eval_r`](@ref) : compute $\mathbf{r}$
  * [`eval_r_J`](@ref) : compute $(\mathbf{r}, \mathbf{J})$
