```julia
GetParams(uc::UnitCell) --> Vector{Param}
```

For legacy purposes.  If you have a `UnitCell` built using the old technique of adding bonds directly, you can get a vector of `Param` using this function, corresponding to each unique bond type already present in `UnitCell`.
