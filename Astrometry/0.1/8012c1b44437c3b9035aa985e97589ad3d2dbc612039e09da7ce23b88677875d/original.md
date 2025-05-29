```
proper_motion(object, pmotion, parallax, rvelocity, pmt, observer)
```

Correct coordinates for proper motion, parallax, radial velocity, and Rømer corrections.

# Arguments

  * `object::Vector{AbstractFloat}`: RA and Dec of object (in radians)
  * `propermo::Vector{AbstractFloat}`: RA and Dec proper motion of object (in radians/year)
  * `parallax::AbstractFloat`: parallax of object (in arcseconds)
  * `rvelocity::AbsractFloat`: radial velocity of object (in km/sec; positive is receding)
  * `propertim::AbstactFloat`: proper motion time interval (in Julian years; at barycenter)
  * `observer::Vector{AbstractFloat}`: position of observer (in AU; from barycenter)

# Returns

  * `object::Vector{AbstractFloat}`: corrected RA and Dec of object
