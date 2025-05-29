#### Type

```
BNGPoint{T<:Real}
```

A struct holding the easting and northing of a point within the British National Grid.

#### Constructors

```
BNGPoint(e, n)
```

Provide eastings `e` and northings `n` in m from the grid origin.

```
BNGPoint(e, n, square)
```

Provide a point within a 100 km square and its name as a two-character string, creating a point with a full reference

```jldoctest
julia> BNGPoint(101, 12345, "OV")
BritishNationalGrid.BNGPoint{Int64}(500101, 512345)

```

!!! note
    An error is thrown if the supplied coordinates do not lie within the valid bounds of the National Grid.


---

```
BNGPoint(; lon=0, lat=0)
```

Convert a WGS84 longitude `lon` and latitude `lat` in degrees, into a grid point.

```jldoctest
julia> BNGPoint(lon=-1.54, lat=55.5)
BNGPoint{Float64}(429158.6966862687, 623009.0927592682)

```

#### Acessing fields

A `BNGPoint` contains the following fields:

  * `e`: Easting in m
  * `n`: Northing in m

These fields are part of the API, and therefore it is safe and expected for users to extract the eastings and northings from a `BNGPoint` like so:

```jldoctest julia> p = BNGPoint(lon=-1.54, lat=55.5) BNGPoint{Float64}(429158.6966862687, 623009.0927592682)

julia> p.e, p.n (429158.6966862687, 623009.0927592682)
