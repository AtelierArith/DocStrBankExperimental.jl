```
iers_era_rotm(m::IERSModel, ut1_d::Number)
```

Compute the CIRF-to-TIRF rotation matrix, according to the IERS conventions `m`, at time  `ut1_d` expressed in UT1 days since J2000 

### References

  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`iers_era`](@ref).
