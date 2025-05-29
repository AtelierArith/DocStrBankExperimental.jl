```
ionizationcrosssection(
     z::Int,
     subshell::Int,
     energy::AbstractFloat,
     edgeenergy::AbstractFloat = edgeenergy(z, subshell),
 )
```

Computes the inner sub-shell ionization cross section for energetic electrons. Asserts if `z` or `subshell` is out of range. Use is hasedge(...) to determine whether an element/sub-shell pair is available.

  * `z` : The atomic number z in the range 1:99
  * `subshell` : The atomic sub-shell being ionized 1->K, 2->L₁, 3->L₂, ..., 9->M₅
  * `energy` : The kinetic energy of the incident electron in eV
  * `edgeenergy` : The edge energy of the sub-shell in eV
