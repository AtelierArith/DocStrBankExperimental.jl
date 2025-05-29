```
WGS84()
```

Construct an object representing the World Geodetic System of 1984, as a dynamic datum - see below for gory details about specific WGS84 frames).

If you're getting positions from a consumer GPS device, you're probably going to have WGS84 by default because it's the datum in which GPS satellites broadcast their position ("broadcast ephemerides").  Note however that many devices can also provide position in a national datum, so you should check your device settings to be sure.

As a special case for low accuracy work (worse than a meter or so), `WGS84` will assume that coordinates supplied without a capture time are in the *latest* frame realization known to Geodesy.jl, WGS84 (G1762). Note that this may not be correct if you're processing historical data, or Geodesy.jl itself is out of date.  For higher accuracy, you should supply a date of capture - either with each coordinate, or explicitly using the `GpsWeek` parameter to the WGS84 type:

```
WGS84{GpsWeek}()
```

Construct an object representing the static WGS84 datum computed using data gathered prior to the given `GpsWeek`.  WGS84 is maintained and updated by the US National Geospatial-Intelligence-Agency (NGA) at irregular intervals to align with the ITRF to within 0.1m (see [1]); if you care about accuracy at that level, you probably want to be solving for position in a different datum, for example, ITRF.  As of 2016, `GpsWeek` should be one out of [0, 730, 873, 1150, 1674, 1762].

Note that the dates of implementation of these frames as broadcast by the satellites are not the same as the associated GPS week - see Ref. [1], table 2.1.  (TODO: Perhaps Geodesy should have a table to figure out which frame to use at a given date?  Does anybody care?)

1. "World Geodetic System 1984", NGA standard NGA.STND.0036*1.0.0*WGS84, 2014-07-08, http://earth-info.nga.mil/GandG/publications/NGA*STND*0036*1*0*0*WGS84/NGA.STND.0036*1.0.0*WGS84.pdf
