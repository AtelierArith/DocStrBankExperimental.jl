```
bandreps(sgnum::Integer, D::Integer=3; 
         allpaths::Bool=false, spinful::Bool=false, timereversal::Bool=true)
```

Returns the elementary band representations (EBRs) as a `BandRepSet` for space group `sgnum` and dimension `D`.

## Keyword arguments

  * `allpaths`: include a minimal sufficient set (`false`, default) or all (`true`)              **k**-vectors.
  * `spinful`: single- (`false`, default) or double-valued (`true`) irreps, as appropriate for            spinless and spinful particles, respectively. Only available for `D=3`.
  * `timereversal`: assume presence (`true`, default) or absence (`false`) of time-reversal                 symmetry.

## References

3D EBRs are obtained from the Bilbao Crystallographic Server's  [BANDREP program](http://www.cryst.ehu.es/cgi-bin/cryst/programs/bandrep.pl); please reference the original research papers noted there if used in published work.
