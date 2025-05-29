```
mphase(jd) -> k
```

### Purpose

Return the illuminated fraction of the Moon at given Julian date(s).

### Arguments

  * `jd`: the Julian ephemeris date.

### Output

The illuminated fraction $k$ of Moon's disk, with $0 ≤ k ≤ 1$. $k = 0$ indicates a new moon, while $k = 1$ stands for a full moon.

### Method

Algorithm from Chapter 46 of "Astronomical Algorithms" by Jean Meeus (Willmann-Bell, Richmond) 1991.  `sunpos` and `moonpos` are used to get positions of the Sun and the Moon, and the Moon distance.  The selenocentric elongation of the Earth from the Sun (phase angle) is then computed, and used to determine the illuminated fraction.

### Example

Plot the illuminated fraction of the Moon for every day in January 2018 with a hourly sampling.  Use [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) for plotting

```julia
using Dates
using Plots
points = DateTime(2018,01,01):Dates.Hour(1):DateTime(2018,01,31,23,59,59);
plot(points, mphase.(jdcnv.(points)))
```

Note that in this calendar month there are two full moons, this event is called [blue moon](https://en.wikipedia.org/wiki/Blue_moon).

### Notes

Code of this function is based on IDL Astronomy User's Library.
