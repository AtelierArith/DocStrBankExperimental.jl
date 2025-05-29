```
generic(i)
```

Return the generic interval, i.e. the number of diatonic steps modulo octave. Unlike [`degree`](@ref), the result respects the sign of the interval (unison=`0`, 2nd up=`1`, 2nd down=`-1`). For pitches, use [`degree`](@ref).

See also: [`degree`](@ref), [`diasteps`](@ref)
