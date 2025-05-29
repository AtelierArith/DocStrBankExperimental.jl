```
UT1Epoch(jd1::T, jd2::T=zero(T); origin=:j2000) where T<:AstroPeriod
```

Construct a UT1Epoch from a Julian date (optionally split into `jd1` and `jd2`). `origin` determines the variant of Julian date that is used. Possible values are:

  * `:j2000`: J2000 Julian date, starts at `2000-01-01T12:00`
  * `:julian`: Julian date, starts at `-4712-01-01T12:00`
  * `:modified_julian`: Modified Julian date, starts at `1858-11-17T00:00`

### Examples

```jldoctest; setup = :(using AstroTime)
julia> UT1Epoch(0.0days, 0.5days)
2000-01-02T00:00:00.000 UT1

julia> UT1Epoch(2.451545e6days, origin=:julian)
2000-01-01T12:00:00.000 UT1
```
