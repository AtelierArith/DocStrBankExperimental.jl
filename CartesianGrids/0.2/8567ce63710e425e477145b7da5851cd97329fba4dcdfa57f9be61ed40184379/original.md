```
plan_implicit_diffusion(a::Real,dims::Tuple,[fftw_flags=FFTW.ESTIMATE])
```

Constructor to set up the forward and inverse operators of `I - a*L` where `L` is the discrete Laplacian (not scaled by grid spacing) and `a` is a real-valued parameter. This can then be applied with the `*` or `` operation on data of the appropriate size.

The `dims` argument can be replaced with data of type `ScalarGridData` to specify the size of the domain.
