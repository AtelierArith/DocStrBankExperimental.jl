```
ct2lst(longitude, jd) -> local_sidereal_time
ct2lst(longitude, tz, date) -> local_sidereal_time
```

### Purpose

Convert from Local Civil Time to Local Mean Sidereal Time.

### Arguments

The function can be called in two different ways.  The only argument common to both methods is `longitude`:

  * `longitude`: the longitude in degrees (east of Greenwich) of the place for which the local sidereal time is desired.  The Greenwich mean sidereal time (GMST) can be found by setting longitude = `0`.

The civil date to be converted to mean sidereal time can be specified either by providing the Julian days:

  * `jd`: this is number of Julian days for the date to be converted.

or the time zone and the date:

  * `tz`: the time zone of the site in hours, positive East of the Greenwich meridian (ahead of GMT).  Use this parameter to easily account for Daylight Savings time (e.g. -4=EDT, -5 = EST/CDT).
  * `date`: this is the local civil time with type `DateTime`.

### Output

The local sidereal time for the date/time specified in hours.

### Method

The Julian days of the day and time is question is used to determine the number of days to have passed since 2000-01-01.  This is used in conjunction with the GST of that date to extrapolate to the current GST; this is then used to get the LST.  See Astronomical Algorithms by Jean Meeus, p. 84 (Eq. 11-4) for the constants used.

### Example

Find the Greenwich mean sidereal time (GMST) on 2008-07-30 at 15:53 in Baltimore, Maryland (longitude=-76.72 degrees).  The timezone is EDT or tz=-4

```jldoctest
julia> using AstroLib, Dates

julia> lst = ct2lst(-76.72, -4, DateTime(2008, 7, 30, 15, 53))
11.356505172312609

julia> sixty(lst)
3-element StaticArraysCore.SVector{3, Float64} with indices SOneTo(3):
 11.0
 21.0
 23.418620325392112
```

Find the Greenwich mean sidereal time (GMST) on 2015-11-24 at 13:21 in Heidelberg, Germany (longitude=08° 43' E).  The timezone is CET or tz=1. Provide `ct2lst` only with the longitude of the place and the number of Julian days.

```jldoctest
julia> using AstroLib, Dates

julia> longitude = ten(8, 43); # Convert longitude to decimals.

julia> # Get number of Julian days. Remember to subtract the time zone in
       # order to convert local time to UTC.

julia> jd = jdcnv(DateTime(2015, 11, 24, 13, 21) - Dates.Hour(1));

julia> lst = ct2lst(longitude, jd) # Calculate Greenwich Mean Sidereal Time.
17.140685171005316

julia> sixty(lst)
3-element StaticArraysCore.SVector{3, Float64} with indices SOneTo(3):
 17.0
  8.0
 26.466615619137883
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
