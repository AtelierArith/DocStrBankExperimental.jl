```
isotopologues(chemical::AbstractChemical, abundance = 1; abtype = :max, threshold = crit(abundance * 1e-4, 1e-4), isobaric = true, mz_tol = crit(0.01, 20e-6), mw_tol = crit(0.01, 20e-6))
isotopologues(formula::AbstractString, abundance = 1; abtype = :max, threshold = crit(abundance * 1e-4, 1e-4), isobaric = true, mz_tol = crit(0.01, 20e-6), mw_tol = crit(0.01, 20e-6), net_charge = 0)
```

Isotopologues of a single `chemical` or `formula` (converted to `Chemical` by `parse_chemical`). 

  * `abundance` sets the abundance of the isotope specified by `abtype`. 

      * `:max`: the most abundant isotopologue
      * `:input`: the input isotopologue
      * other: the final abundances are repressented as proportion.
  * `threshold` can be a number or criteria, representing the lower limit of abundance.
  * `isobaric` determines whether groups isobars and creates `Isobars` or not.
  * `mz_tol`: tolerance of m/z for isobars.
  * `mw_tol`: tolerance of molecular weight for isobars.
  * `net_charge`: charges (positive or negative) of `formula`.
