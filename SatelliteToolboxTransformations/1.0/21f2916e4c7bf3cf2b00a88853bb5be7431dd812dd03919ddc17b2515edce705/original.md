```
r_eci_to_eci([T, ]ECIo, ECIf, jd_utc::Number[, eop]) -> T
r_eci_to_eci([T, ]ECIo, jd_utco::Number, ECIf, jd_utcf::Number[, eop]) -> T
```

Compute the rotation from an Earth-Centered Inertial (ECI) reference frame `ECIo` to another ECI reference frame `ECIf`. If the origin and destination frame contain only one *of date* frame, the first signature is used and the Julian Day `jd_utc` [UTC] is the epoch of this frame. On the other hand, if the origin and destination frame contain two *of date* frame`¹`, e.g. TOD => MOD, the second signature must be used in which the Julian Day `jd_utco` [UTC] is the epoch of the origin frame and the Julian Day `jd_utcf` [UTC] is the epoch of the destination frame. The rotation description that will be used is given by `T`, which can be `DCM` or `Quaternion`. The algorithm might also require the Earth Orientation Parameters (EOP) `eop` depending on the source and destination frames.

!!! note
    For more information, including how to specify the origin and destination reference frames, see the **Extended Help**.


`¹`: TEME is an *of date* frame.

# Returns

  * `T`: Rotation that aligns the origin ECI reference frame with the destination ECI   reference frame.

# Extended Help

## Rotation Description

The rotation can be described by Direction Cosine Matrices (DCMs) or Quaternions. This is selected by the parameter `T`.

The possible values are:

  * `DCM`: The rotation will be described by a Direction Cosine Matrix.
  * `Quaternion`: The rotation will be described by a Quaternion.

If no value is specified, it falls back to `DCM`.

## Conversion Model

The model that will be used to compute the rotation is automatically inferred given the selection of the origin and destination frames. **Notice that mixing IAU-76/FK5 and IAU-2006/2010 frames is not supported.**

## Supported ECI Reference Frames

The supported ECI frames for both origin `ECIo` and destination `ECIf` are:

  * `TEME()`: ECI will be selected as the True Equator Mean Equinox (TEME) reference frame.
  * `TOD()`: ECI will be selected as the True of Date (TOD).
  * `MOD()`: ECI will be selected as the Mean of Date (MOD).
  * `J2000()`: ECI will be selected as the J2000 reference frame.
  * `GCRF()`: ECI will be selected as the Geocentric Celestial Reference Frame (GCRF).
  * `CIRS()`: ECEF will be selected as the Celestial Intermediate Reference System (CIRS).
  * `ERS()`: ECI will be selected as the Earth Reference System (ERS).
  * `MOD06()`: ECI will be selected as the Mean of Date (MOD) according to the definition in   IAU-2006/2010 theory.
  * `MJ2000()`: ECI will be selected as the J2000 mean equatorial frame (MJ2000).

!!! note
    The frames `MOD()` and `MOD06()` are virtually the same. However, we selected different names to make clear which theory are being used since mixing transformation between frames from IAU-76/FK5 and IAU-2006/2010 must be performed with caution.


## Earth Orientation Parameters (EOP)

The conversion between the frames might depend on EOP Data (see [`fetch_iers_eop`](@ref) and [`read_iers_eop`](@ref)). If IAU-76/FK5 model is used, the type of `eop` must be [`EopIau1980`](@ref). Otherwise, if IAU-2006/2010 model is used, the type of `eop` must be [`EopIau2000A`](@ref). The following table shows the requirements for EOP data given the selected frames.

| Model                       | ECIo     | ECIf     | EOP Data      | Function Signature |
|:--------------------------- |:-------- |:-------- |:------------- |:------------------ |
| IAU-76/FK5                  | `GCRF`   | `J2000`  | EOP IAU1980   | First              |
| IAU-76/FK5                  | `GCRF`   | `MOD`    | EOP IAU1980   | First              |
| IAU-76/FK5                  | `GCRF`   | `TOD`    | EOP IAU1980   | First              |
| IAU-76/FK5                  | `GCRF`   | `TEME`   | EOP IAU1980   | First              |
| IAU-76/FK5                  | `J2000`  | `GCRF`   | EOP IAU1980   | First              |
| IAU-76/FK5                  | `J2000`  | `MOD`    | Not required  | First              |
| IAU-76/FK5                  | `J2000`  | `TOD`    | Not required  | First              |
| IAU-76/FK5                  | `J2000`  | `TEME`   | Not required  | First              |
| IAU-76/FK5                  | `MOD`    | `GCRF`   | EOP IAU1980   | First              |
| IAU-76/FK5                  | `MOD`    | `J2000`  | Not required  | First              |
| IAU-76/FK5                  | `MOD`    | `TOD`    | Not required  | Second             |
| IAU-76/FK5                  | `MOD`    | `TEME`   | Not required  | Second             |
| IAU-76/FK5                  | `TOD`    | `GCRF`   | EOP IAU1980   | First              |
| IAU-76/FK5                  | `TOD`    | `J2000`  | Not required  | First              |
| IAU-76/FK5                  | `TOD`    | `MOD`    | Not required  | Second             |
| IAU-76/FK5                  | `TOD`    | `TEME`   | Not required  | Second             |
| IAU-76/FK5                  | `TEME`   | `GCRF`   | EOP IAU1980   | First              |
| IAU-76/FK5                  | `TEME`   | `J2000`  | Not required  | First              |
| IAU-76/FK5                  | `TEME`   | `MOD`    | Not required  | Second             |
| IAU-76/FK5                  | `TEME`   | `TOD`    | Not required  | Second             |
| IAU-2006/2010 CIO-based     | `GCRF`   | `CIRS`   | Not required¹ | First              |
| IAU-2006/2010 CIO-based     | `CIRS`   | `CIRS`   | Not required¹ | Second             |
| IAU-2006/2010 Equinox-based | `GCRF`   | `MJ2000` | Not required  | First²             |
| IAU-2006/2010 Equinox-based | `GCRF`   | `MOD06`  | Not required  | First              |
| IAU-2006/2010 Equinox-based | `GCRF`   | `ERS`    | Not required³ | First              |
| IAU-2006/2010 Equinox-based | `MJ2000` | `GCRF`   | Not required  | First²             |
| IAU-2006/2010 Equinox-based | `MJ2000` | `MOD06`  | Not required  | First              |
| IAU-2006/2010 Equinox-based | `MJ2000` | `ERS`    | Not required³ | First              |
| IAU-2006/2010 Equinox-based | `MOD06`  | `GCRF`   | Not required  | First              |
| IAU-2006/2010 Equinox-based | `MOD06`  | `MJ2000` | Not required  | First              |
| IAU-2006/2010 Equinox-based | `MOD06`  | `ERS`    | Not required³ | First              |
| IAU-2006/2010 Equinox-based | `ERS`    | `GCRF`   | Not required³ | First              |
| IAU-2006/2010 Equinox-based | `ERS`    | `MJ2000` | Not required³ | First              |
| IAU-2006/2010 Equinox-based | `ERS`    | `MOD06`  | Not required³ | First              |

`¹`: In this case, the terms that account for the free-core nutation and time dependent effects of the Celestial Intermediate Pole (CIP) position with respect to the GCRF will not be available, reducing the precision.

`²`: The transformation between GCRF and MJ2000 is a constant rotation matrix called bias. Hence, the date does not modify it. However, this signature was kept to avoid complications in the API.

`³`: In this case, the terms that corrects the nutation in obliquity and in longitude due to the free core nutation will not be available, reducing the precision.

!!! info
    In this function, if EOP corrections are not provided, MOD and TOD frames will be computed considering the original IAU-76/FK5 theory. Otherwise, the corrected frame will be used.


# Examples

```julia-repl
julia> eop_iau1980 = fetch_iers_eop(Val(:IAU1980));

julia> r_eci_to_eci(DCM, GCRF(), J2000(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau1980)
DCM{Float64}:
  1.0          -4.71326e-12   1.53474e-9
  4.71332e-12   1.0          -3.53979e-9
 -1.53474e-9    3.53979e-9    1.0

julia> r_eci_to_eci(Quaternion, TEME(), GCRF(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau1980)
Quaternion{Float64}:
  + 0.999999 + 1.83013e-5⋅i + 0.000665304⋅j - 0.00151324⋅k

julia> r_eci_to_eci(TOD(), date_to_jd(1986,6,19,21,35,0), TOD(), date_to_jd(1987,5,19,3,0,0), eop_iau1980)
DCM{Float64}:
 1.0          -0.000224088  -9.73787e-5
 0.000224087   1.0          -5.80065e-6
 9.738e-5      5.77883e-6    1.0

julia> r_eci_to_eci(Quaternion, TOD(), JD_J2000, MOD(), JD_J2000, eop_iau1980)
Quaternion{Float64}:
  + 1.0 - 1.40025e-5⋅i + 1.34736e-5⋅j - 3.10785e-5⋅k

julia> r_eci_to_eci(J2000(), TEME(), date_to_jd(1986,6,19,21,35,0))
DCM{Float64}:
  0.999995    0.0030265    0.00133055
 -0.00302645  0.999995    -3.86125e-5
 -0.00133066  3.45854e-5   0.999999

julia> eop_iau2000a = fetch_iers_eop(Val(:IAU2000A));

julia> r_eci_to_eci(CIRS(), GCRF(), date_to_jd(1986,6,19,21,35,0), eop_iau2000a)
DCM{Float64}:
 0.999999     3.88389e-8  -0.00133066
 7.18837e-9   1.0          3.45897e-5
 0.00133066  -3.45897e-5   0.999999

julia> r_eci_to_eci(Quaternion, CIRS(), GCRF(), date_to_jd(1986,6,19,21,35,0), eop_iau2000a)
Quaternion{Float64}:
  + 1.0 + 1.72949e-5⋅i + 0.000665332⋅j + 7.91263e-9⋅k
```
