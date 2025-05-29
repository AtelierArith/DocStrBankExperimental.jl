```
calc_bandreps(sgnum::Integer, Dᵛ::Val{D}=Val(3);
              timereversal::Bool=true,
              allpaths::Bool=false,
              explicitly_real::Bool=timereversal)
```

Compute the band representations of space group `sgnum` in dimension `D`, returning a `BandRepSet`.

## Keyword arguments

  * `timereversal` (default, `true`): whether the irreps used to induce the band representations are assumed to be time-reversal invariant (i.e., are coreps, see  [`realify`](@ref)).
  * `allpaths` (default, `false`): whether the band representations are projected to all distinct **k**-points returned by `lgirreps` (`allpaths = false`), including high-symmetry **k**-lines and -plane, or only to the maximal **k**-points (`allpaths = true`), i.e., just to high-symmetry points.
  * `explicitly_real` (default, `timereversal`): whether, if `timereversal = true`, to ensure that the site symmetry irreps accompanying the band representations are chosen to be explicitly real (or "physically" real; see [`physical_realify`](@ref)). This is helpful for subsequent analysis of the action of time-reversal symmetry.

## Notes

All band representations associated with maximal Wyckoff positions are returned,  irregardless of whether they are elementary (i.e., no regard is made to whether the band representation is "composite"). As such, the returned band representations generally are a superset of the set of elementary band representations (and so contain all elementary band representations).

## Implementation

The implementation is based on Cano, Bradlyn, Wang, Elcoro, et al., [Phys. Rev. B **97**, 035139 (2018)](https://doi.org/10.1103/PhysRevB.97.035139), Sections II.C-D.
