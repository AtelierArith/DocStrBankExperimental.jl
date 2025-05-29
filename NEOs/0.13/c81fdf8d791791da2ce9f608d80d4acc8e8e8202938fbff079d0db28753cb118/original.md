```
pv2kep(xas::Vector{U}; μ::T = μ_S, jd::T = JD_J2000,
       frame::Symbol = :equatorial) where {T <: Real, U <: Number}
```

Compute the orbital elements of the NEO with state vector `xas`. Return an `OsculatingElements` object.

See also [`equatorial2ecliptic`](@ref), [`eccentricity`](@ref), [`semimajoraxis`](@ref), [`timeperipass`](@ref), [`longascnode`](@ref), [`argperi`](@ref) and [`inclination`](@ref).

# Arguments

  * `xas::Vector{U}`: state vector of the asteroid `[x, y, z, v_x, v_y, v_z]`.
  * `μ_S::T`: mass parameter of the central body (Sun).
  * `jd::T`: orbit epoch of reference in julian days.
  * `frame::Symbol`: plane of reference (`:equatorial` or `:ecliptic`).
