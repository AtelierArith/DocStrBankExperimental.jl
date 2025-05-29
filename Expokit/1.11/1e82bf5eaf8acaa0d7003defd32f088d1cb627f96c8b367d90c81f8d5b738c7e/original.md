```
phimv{T}(t, A, u, vec; [tol], [m], [norm], [anorm])
```

Calculate the solution of a nonhomogeneous linear ODE problem with constant input $w = e^{tA}v + tφ(tA)u$ using the Krylov subspace approximation.

# Input

  * `A`   – matrix which can be dense or sparse
  * `u`   – vector, constant input of the ODE
  * `vec` – vector on which the matrix exponential of $A$ is applied
  * `tol` – (optional, default: 1e-7) the requested accuracy tolerance on $w$
  * `m`   – (optional, default: min(30, n)) maximum size of the Krylov basis

---

```
[w, err] = phiv( t, A, u, v, tol, m )
PHIV computes an approximation of ``w = exp(tA)v + t φ(tA)u``
for a general matrix A using Krylov subspace projection techniques.
Here, ``φ(z) = (\exp(z)-1)/z`` and ``w`` is the solution of the
nonhomogeneous linear ODE problem ``w' = Aw + u``, ``w(0) = v``.
It does not compute the matrix functions in isolation but instead,
it computes directly the action of these functions on the
operand vectors. This way of doing so allows for addressing large
sparse problems. The matrix under consideration interacts only
via matrix-vector products (matrix-free method).

Roger B. Sidje (rbs@maths.uq.edu.au)
EXPOKIT: Software Package for Computing Matrix Exponentials.
ACM - Transactions On Mathematical Software, 24(1):130-156, 1998
```
