```julia
function fbands(sr :: Int,
                wl :: Int,
         bandwidth :: IntOrReal;
      DC :: Bool = false)
```

Return a vector of Frequencies (in Hz) to which the bins created by a call to function [`bbands`](@ref) with the same arguments correspond.

**See**: [`bbands`](@ref).

**See also**: [`bands`](@ref).
