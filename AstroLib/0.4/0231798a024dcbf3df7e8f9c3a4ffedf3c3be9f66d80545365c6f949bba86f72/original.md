```
nutate(jd) -> long, obliq
```

### Purpose

Return the nutation in longitude and obliquity for a given Julian date.

### Arguments

  * `jd`: Julian ephemeris date, it can be either a scalar or a vector

### Output

The 2-tuple `(long, obliq)`, where

  * `long`: the nutation in longitude
  * `obl`: the nutation in latitude

If `jd` is an array, `long` and `obl` are arrays of the same length.

### Method

Uses the formula in Chapter 22 of "Astronomical Algorithms" by Jean Meeus (1998, 2nd ed.) which is based on the 1980 IAU Theory of Nutation and includes all terms larger than 0.0003".

### Example

  * Find the nutation in longitude and obliquity 1987 on Apr 10 at 0h.  This is example 22.a from Meeus

    ```jldoctest
    julia> using AstroLib

    julia> jd = jdcnv(1987, 4, 10);

    julia> nutate(jd)
    (-3.787931077110494, 9.44252069864449)
    ```
  * Plot the daily nutation in longitude and obliquity during the 21st century. Use [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) for plotting.

    ```julia
    using Dates
    using Plots
    years = DateTime(2000):DateTime(2100);
    long, obl = nutate(jdcnv.(years));
    plot(years, long); plot(years, obl)
    ```

You can see both the dominant large scale period of nutation, of 18.6 years, and smaller oscillations with shorter periods.

### Notes

Code of this function is based on IDL Astronomy User's Library.
