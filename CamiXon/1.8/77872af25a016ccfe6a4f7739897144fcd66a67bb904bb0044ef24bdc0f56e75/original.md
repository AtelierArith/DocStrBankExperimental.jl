```
castInE(E::T, def::Def{T}) where T<:Real
```

Create and initialize the energy object [`InE`](@ref) according to the  specifications given in the [`Def`](@ref) object.

  * `.Emin` : lower energy limit (`::T`)
  * `.E` : trial energy (`::T`)
  * `.Emax` : upper energy limit (`::T`)
  * `.ΔE` : difference with respect to previous E used to calculate current E  (`::T`)
