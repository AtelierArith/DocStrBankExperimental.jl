```
eigenfrequencies(m::LinearLayeredModel, freq=1.0; kwargs...) -> freqs
```

Compute the eigenfrequencies of normal modes for the model `m`. `m` must be a `LinearLayeredModel` from `SeisModels`.

Eigenfrequencies are returned as an `OrderedDict` where the keys are a tuple of the radial order $n$, mode type (`:S` for spheroidal, `:T` for toroidal, `:C` for inner core toroidal), and angular order ℓ.

For example, to retrieve ₀S₂, do `freqs[(0,:S,2)]`, and for ₃T₈ write `freqs[(3,:T,8)]`.  The syntax `freqs[3,:T,8]` is also allowed.

### Keyword arguments

#### Mode selection

  * `radial=true`: Calculate (or not) radial modes.  In this case, `nmin` and `nmax` are ignored.
  * `spheroidal=true`: Calculate (or not) spheroidal modes.
  * `toroidal=true`: Calculate (or not) toroidal modes.
  * `ic_toroidal=true`: Calculate (or not) inner core toroidal modes.

#### Calculation parameters

  * `eps=1e-10`: Accuracy of the integration scheme.  Eigenfrequencies are accurate relatively to about `2eps` to `3eps`.  `eps` can be `1e-7` for frequencies less than 100 mHz (periods over 10 s); for frequencies of 100 to 200 mHz (periods 5 to 10 s), `eps` should be between `1e-12` and `1e-10`.
  * `wgrav=10`: Frequency in mHz above which gravitational terms are neglected.
  * `lmin=1`, `lmax=20`: Minimum and maximum angular order of modes.
  * `wmin=0.0`, `wmax=166.0`: Minimum and maximum mode eigenfrequencies to consider.
  * `nmin=0`, `nmax=10`: Minimum and maximum dispersion branch numbers to compute.
