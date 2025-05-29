```
NotYetTreatedParallel{C,S} <: TrendParallel{C,S}
```

Assume a parallel trends assumption holds between any group that received the treatment relatively early and any group that received the treatment relatively late (or never receved). See also [`notyettreated`](@ref).

# Fields

  * `e::Tuple{Vararg{ValidTimeType}}`: group indices for units that received the treatment relatively late.
  * `ecut::Tuple{Vararg{ValidTimeType}}`: user-specified period(s) when units in a group in `e` started to receive treatment or show anticipation effects.
  * `c::C`: an instance of [`ParallelCondition`](@ref).
  * `s::S`: an instance of [`ParallelStrength`](@ref).

!!! note
    `ecut` could be different from `minimum(e)` if

      * never-treated groups are included and use indices with smaller values;
      * the sample has a rotating panel structure with periods overlapping with some others.

