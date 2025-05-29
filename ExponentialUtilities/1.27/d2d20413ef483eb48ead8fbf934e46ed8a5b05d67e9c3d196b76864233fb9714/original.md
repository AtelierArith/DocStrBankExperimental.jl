```
phiv_timestep(ts,A,B[;adaptive,tol,kwargs...]) -> U
```

Evaluates the linear combination of phi-vector products using time stepping

$$
u = \varphi_0(tA)b_0 + t\varphi_1(tA)b_1 + \cdots + t^p\varphi_p(tA)b_p
$$

`ts` is an array of time snapshots for u, with `U[:,j] ≈ u(ts[j])`. `ts` can also be just one value, in which case only the end result is returned and `U` is a vector.

The time stepping formula of Niesen & Wright is used [^1]. If the time step `tau` is not specified, it is chosen according to (17) of Niesen & Wright. If `adaptive==true`, the time step and Krylov subspace size adaptation scheme of Niesen & Wright is used, the relative tolerance of which can be set using the keyword parameter `tol`. The delta and gamma parameters of the adaptation scheme can also be adjusted.

When encountering a happy breakdown in the Krylov subspace construction, the time step is set to the remainder of the time interval since time stepping is no longer necessary.

Set `verbose=true` to print out the internal steps (for debugging). For the other keyword arguments, consult `arnoldi` and `phiv`, which are used internally.
