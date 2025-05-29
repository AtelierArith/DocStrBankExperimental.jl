```
struct TransientMDEIMReduction{A,R<:Reduction{A,EuclideanNorm}} <: AbstractMDEIMReduction{A}
  reduction::R
  combine::Function
end
```

MDEIM struct employed in transient problems. The field `combine` is a function used to group the reductions relative to the various Jacobians(in general, more than one in transient problems) in a smart way. We consider, for example, the ODE

$\tfrac{du}{dt} - \nu \Delta u = f \ \ \text{in} \ \ Ω \times [0,T]$

subject to initial/boundary conditions. Upon applying a FE discretization in space, and a `θ`-method in time, one gets the space-time system

$A_{\theta} u_{\theta} = f_{\theta}$

where

$$
A_{\theta} = \begin{bmatrix}
A_1 + M / (\theta \Delta t) & & & & & \\
- M / (\theta \Delta t) & A_2 + M / (\theta \Delta t) & & & & \\
& - M / (\theta \Delta t) & A_3 + M / (\theta \Delta t) & & & \\
& & \ddots & \ddots & & \\
& & & & - M / (\theta \Delta t) & A_n + M / (\theta \Delta t)
\end{bmatrix};
$$

$$
u_{\theta} = \left[(1-\theta)u_0 + \theta u_1, \hdots, (1-\theta)u_{n-1} + \theta u_n\right]^T;
$$

$$
f_{\theta} = \left[f_1, \hdots, f_n\right]^T;
$$

$$
A_k = A(t_{k-1} + \theta \Delta t);
$$

$$
f_k = f(t_{k-1} + \theta \Delta t).
$$

Note: instead of multiplying $A_{\theta}$ by $u_{\theta}$, we multiply $\tilde{A}_{\theta}$ by $u$, where

$$
\tilde{A}_{\theta} = tridiag((1-\theta)A_{k-1} - M / \Delta t, \theta A_k + M / \Delta t, 0).
$$

We now denote with $\Phi$ and $\Psi$ the spatial and temporal basis obtained by reducing the snapshots associated to the state variable $u$. The Galerkin projection of the space-time system is equal to $\hat{A}_{\theta}\hat{u} = \hat{f}_{\theta}$, where $\hat{u}$ is the unknown, and

$$
\begin{align*}
\hat{A}_{\theta} &= \sum\limits_{k=1}^{n-1} ( (1-θ) \Phi^T A_k \Phi - \Phi^T M \Phi / \Delta t) \otimes \Psi[k-1,:]^T \Psi[k,:]
  + \sum\limits_{k=1}^n (\theta \Phi^T A_k \Phi + \Phi^T M \Phi / \Delta t) \otimes \Psi[k,:]^T \Psi[k,:] \\
  &= \theta A_{backwards} + (1-\theta)A_{forwards} + (M_{backwards} + M_{forwards}) / \Delta t \\
\hat{f}_{\theta} &= \sum\limits_{k=1}^n \Phi^T f_k \otimes \Psi[k,:]
\end{align*}
$$

We notice that the expression of $\hat{A}_{\theta}$ can be written in a more general form as

$$
\hat{A}_{\theta} = combine_A(A_{backwards},A_{forwards}) + combine_M(M_{backwards},M_{forwards}),
$$

where combine*A and combine*M are two function specific to A and M:

$$
\begin{align*}
combine_A(x,y) &= \theta y + (1-\theta)y \\
combine_M(x,y) &= (x - y) / \Delta t
\end{align*}
$$

The same can be said of any time marching scheme. This is the meaning of the function `combine`. Note that for a time marching with $p$ interpolation points (e.g. for $\theta$ method, $p = 2$) the `combine` functions will have to accept $p$ arguments.
