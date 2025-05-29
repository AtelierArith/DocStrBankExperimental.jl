```
SolutionCertificate
```

Result of [`certify`](@ref) for a single solution. Contains the initial solutions and if the certification was successfull a vector of complex intervals where the true solution is contained in. The complex intervals are given as an `Arblib.AcbMatrix`. The `Arblib.AcbMatrix` is printed in the default format of `Arblib`. This means that, if the midpoint of an interval can't be represented with sufficiently many correct digits, `Arblib` will not print the midpoint. Instead, it will print an interval of the form `[+/- r]`, where `r` will be an upper bound for the absolute value of the ball. An enclosure of the correct interval can be printed as follows.

```julia
Base.show(certificate::SolutionCertificate; digits = 16, more = true)
```

This uses the [`ARB_STR_MORE`](https://flintlib.org/doc/arb.html#c.arb_get_str) functionality in `Flint` with `16` digits.
