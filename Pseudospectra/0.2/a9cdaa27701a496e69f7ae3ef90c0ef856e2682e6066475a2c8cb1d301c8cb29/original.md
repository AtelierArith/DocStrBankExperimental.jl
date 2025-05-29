```
ArpackOptions{T}(; nev=6, ncv=0, which=:LM,
                                       tol=zero(T),maxiter=300,
                                       v0=Vector{T}(0), have_v0=false,
                                       sigma=nothing)
```

constructs an object to manage the Arnoldi scheme; see the documentation for `eigs` in the `Arpack` package for the meaning of fields.
