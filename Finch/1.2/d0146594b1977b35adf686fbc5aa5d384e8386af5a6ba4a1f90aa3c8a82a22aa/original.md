parallel(ext, device=CPU(nthreads()), schedule=static_schedule())

A dimension `ext` that is parallelized over `device` using the `schedule`. The `ext` field is usually `_`, or dimensionless, but can be any standard dimension argument.
