```
bremsstrahlung(::Type{<:NeXLBremsstrahlung}, e::AbstractFloat, e0::AbstractFloat, elm::Element)
```

Calcualtes the Bremsstrahlung (continuum) at an energy `e` for an incident electron of `e0` in the element `elm`.

The supported models include:  Kramers1923, Lifshin1974, Reed1975, Smith1975, Small1987, Trincavelli1997,  Castellano2004a, Castellano2004b

Evaluating the models I find that Castellano2004a, Trincavelli1997 work well with the Riveros1993 matrix correction algorithm and the AP33Tabulation window.  Smith1975 works surprisigly well with the CitZAF matrix correction model. Other old models based on Si(Li) data tend to not do too well at lower energies.  This shouldn't surprise anyone as these models were often based on data from Be window detectors.  Castellano2004a and Trincavelli1997 were designed around the Riveros1993 matrix correction model and don't perform well using CitZAF.

My current recommendation is either Castellano2004a or Riveros1993.
