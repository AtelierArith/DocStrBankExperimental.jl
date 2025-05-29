```
update_derived!(electrolyte::ElectrolyteData)
```

Update derived electrolyte data. This needs to be called in order to update fields `Mrel`, `vrel`, `barv`, `tildev`, `RT`, `γ_bulk` of `ElectrolyteData` after changing some of the other parameters.

Called on the passed electrolyte data by [`PNPSystem`](@ref),  [`PBSystem`](@ref),  [`dlcapsweep`](@ref),  [`ivsweep`](@ref),  [`cvsweep`](@ref).
