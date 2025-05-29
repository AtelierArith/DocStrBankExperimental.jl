```
transfer_spectrum(above::InfiniteMPS; below=above, tol=Defaults.tol, num_vals=20,
                       sector=first(sectors(oneunit(left_virtualspace(above, 1)))))
```

Calculate the partial spectrum of the left mixed transfer matrix corresponding to the overlap of a given `above` state and a `below` state. The `sector` keyword argument can be used to specify a non-trivial total charge for the transfer matrix eigenvectors. Specifically, an auxiliary space `ℂ[typeof(sector)](sector => 1)'` will be added to the domain of each eigenvector. The `tol` and `num_vals` keyword arguments are passed to `KrylovKit.eigolve`
