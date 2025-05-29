```
planet_coords(date, num)
```

### Purpose

Find right ascension and declination for the planets when provided a date as input.

### Explanation

This function uses the [`helio`](@ref) to get the heliocentric ecliptic coordinates of the planets at the given date which it then converts these to geocentric ecliptic coordinates ala "Astronomical Algorithms" by Jean Meeus (1991, p 209). These are then converted to right ascension and declination using [`euler`](@ref).

The accuracy between the years 1800 and 2050 is better than 1 arcminute for the terrestial planets, but reaches 10 arcminutes for Saturn. Before 1850 or after 2050 the accuracy can get much worse.

### Arguments

  * `date`: Can be either a single date or an array of dates. Each element can be either a `DateTime` type or Julian Date. It can be a scalar or vector.
  * `num`: integer denoting planet number, scalar or vector 1 = Mercury, 2 = Venus, ... 9 = Pluto. If not in that change, then the program will throw an error.

### Output

  * `ra`: right ascension of planet(J2000), in degrees
  * `dec`: declination of the planet(J2000), in degrees

### Example

Find the RA, Dec of Venus on 1992 Dec 20

```jldoctest
julia> using AstroLib, Dates

julia> adstring(planet_coords(DateTime(1992,12,20),2))
" 21 05 02.8  -18 51 41"
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
