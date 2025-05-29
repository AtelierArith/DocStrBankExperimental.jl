```
amplitude_db(c::Cut, ipol::Int)
amplitude_db(c::Cut, polsymb::Symbol = :copol)
amplitude_db(c::Cut, polstr::String = "copol")
```

Return a matrix of amplitudes in dB for some choice of polarization in the cut. Legal values for `ipol` are 1, 2, or 3, the latter only being legal if there are three polarization components present in the cut.  Legal values for `polstr` are "copol" (the default) and "xpol".  Capitalization is not significant. Legal values for `polsymb` are `:copol` and `:xpol`.  Again, capitalization is not significant.  Copol is defined as the polarization with maximum amplitude at θ = ϕ = 0.
