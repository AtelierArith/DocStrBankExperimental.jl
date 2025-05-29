```
r_ecef_to_ecef([T, ]ECEFo, ECEFf, jd_utc::Number, eop) -> T
```

Compute the rotation from an Earth-Centered, Earth-Fixed (ECEF) reference frame `ECEFo` to another ECEF reference frame `ECEFf` at the Julian Day `jd_utc` [UTC]. The rotation description that will be used is given by `T`, which can be `DCM` or `Quaternion`. The algorithm also requires the Earth Orientation Parameters (EOP) `eop`.

!!! note
    For more information, including how to specify the origin and destination reference frames, see the **Extended Help**.


# Returns

  * `T`: Rotation entity that aligns the `ECEFo` reference frame with the `ECEFf` reference   frame at the epoch `jd_utc`.

# Extended Help

## Rotation Description

The rotation can be described by Direction Cosine Matrices (DCMs) or Quaternions. This is selected by the parameter `T`. The possible values are:

  * `DCM`: The rotation will be described by a Direction Cosine Matrix.
  * `Quaternion`: The rotation will be described by a Quaternion.

If no value is specified, it falls back to `DCM`.

## Conversion Model

The model that will be used to compute the rotation is automatically inferred given the selection of the origin and destination frames. **Notice that mixing IAU-76/FK5 and IAU-2006/2010 frames is not supported.**

## Supported ECEF Reference Frames

The supported ECEF frames for both origin `ECEFo` and destination `ECEFf` are:

  * `ITRF()`: ECEF will be selected as the International Terrestrial Reference Frame (ITRF).
  * `PEF()`: ECEF will be selected as the Pseudo-Earth Fixed (PEF) reference frame   (IAU-76/FK5).
  * `TIRS()`: ECEF will be selected as the Terrestrial Intermediate Reference System (TIRS)   (IAU-2006/2010).

## Earth Orientation Parameters (EOP)

The conversion between the supported ECEF frames **always** depends on EOP (see [`fetch_iers_eop`](@ref) and [`read_iers_eop`](@ref)). If IAU-76/FK5 model is used, the type of `eop` must be [`EopIau1980`](@ref). Otherwise, if IAU-2006/2010 model is used, the type of `eop` must be [`EopIau2000A`](@ref).

## Examples

```julia-repl
julia> eop_iau1980 = fetch_iers_eop();

julia> r_ecef_to_ecef(PEF(), ITRF(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau1980)
DCM{Float64}:
  1.0          0.0         -4.34677e-7
 -6.29476e-13  1.0         -1.44815e-6
  4.34677e-7   1.44815e-6   1.0

julia> r_ecef_to_ecef(Quaternion, PEF(), ITRF(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau1980)
Quaternion{Float64}:
  + 1.0 - 7.24073e-7⋅i + 2.17339e-7⋅j - 0.0⋅k

julia> eop_iau2000A = fetch_iers_eop(Val(:IAU2000A));

julia> r_ecef_to_ecef(TIRS(), ITRF(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau2000A)
DCM{Float64}:
  1.0          3.08408e-11  -4.34677e-7
 -3.14703e-11  1.0          -1.44815e-6
  4.34677e-7   1.44815e-6    1.0

julia> r_ecef_to_ecef(Quaternion, TIRS(), ITRF(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau2000A)
Quaternion{Float64}:
  + 1.0 - 7.24073e-7⋅i + 2.17339e-7⋅j + 1.55778e-11⋅k
```
