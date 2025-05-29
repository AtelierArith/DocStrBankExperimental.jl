```
freeprecess!(A, B, t, M0, T1, T2, Δf)
freeprecess!(A, B, spin, t, [nothing])
freeprecess!(A, B, spinmc, t, [workspace])
freeprecess!(A, B, spin, t, grad, [nothing])
freeprecess!(A, B, spinmc, t, grad, [workspace])
```

Simulate free-precession, overwriting `A` and `B` (in-place version of [`freeprecess`](@ref)).
