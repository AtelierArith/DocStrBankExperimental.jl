```
phase_deg(c::Cut, ipol::Int)
phase_deg(c::Cut, polsymb::Symbol)
phase_deg(c::Cut, polstr::String = "copol")
```

Return a matrix of phases in degrees for some choice of polarization in the cut. Legal values for `ipol` are 1, 2, or 3.  Legal values for `polstr` are "copol" (the default) and "xpol" (capitalization is not significant).  Legal values of `polsymb` are `:copol` and `:xpol`.  Again, capitalization is not significant. The returned value is a `Matrix{Float64}` with `length(get_theta(cut))` rows and `length(get_phi(cut))` columns.
