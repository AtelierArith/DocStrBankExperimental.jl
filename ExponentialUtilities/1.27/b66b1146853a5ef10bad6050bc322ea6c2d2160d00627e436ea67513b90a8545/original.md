```
expv_timestep(ts,A,b[;adaptive,tol,kwargs...]) -> U
```

Evaluates the matrix exponentiation-vector product using time stepping

$$
u = \exp(tA)b
$$

`ts` is an array of time snapshots for u, with `U[:,j] ≈ u(ts[j])`. `ts` can also be just one value, in which case only the end result is returned and `U` is a vector.

The time stepping formula of Niesen & Wright is used [^1]. If the time step `tau` is not specified, it is chosen according to (17) of Niesen & Wright. If `adaptive==true`, the time step and Krylov subspace size adaptation scheme of Niesen & Wright is used, the relative tolerance of which can be set using the keyword parameter `tol`. The delta and gamma parameters of the adaptation scheme can also be adjusted.

Set `verbose=true` to print out the internal steps (for debugging). For the other keyword arguments, consult `arnoldi` and `phiv`, which are used internally.

Note that this function is just a special case of `phiv_timestep` with a more intuitive interface (vector `b` instead of a n-by-1 matrix `B`).

[^1]: Niesen, J., & Wright, W. (2009). A Krylov subspace algorithm for evaluating the φ-functions in exponential integrators. arXiv preprint arXiv:0907.4631.
