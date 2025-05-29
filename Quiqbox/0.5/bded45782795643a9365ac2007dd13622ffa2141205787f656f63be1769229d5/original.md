```
genCanOrbitals(fVars::HFfinalVars{T, D, <:Any, NN}; 
               roundAtol::Real=getAtolVal(T)) where {T, D, NN} -> 
NTuple{2, Vector{CanOrbital{T, D, NN}}}
```

Generate the occupied and unoccupied canonical orbitals from the result of a Hartree–Fock  approximation `fVars`. Each parameter stored in the constructed [`CanOrbital`](@ref) will  be rounded to the nearest multiple of `roundAtol`; when `roundAtol` is set to `NaN`, no  rounding will be performed.
