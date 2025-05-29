```
RingInfo
```

Information about a ring of pixels, i.e., the set of pixels on a Healpix map which have the same colatitude. The type is "mutable", so that one object can begin reused many times without further memory allocations.

The list of fields defined in this structure is the following:

  * `ring`: an integer index, running from
  * `firstPixIdx`: index of the first pixel (using the `RING` scheme) belonging to this ring
  * `numOfPixels`: number of consecutive pixels within the ring
  * `colatitude_rad`: value of the colatitude for this ring (in radians)
  * `shifted`: Boolean flag; it is `true` if the longitude of the first pixel in the ring is not zero.

# References

See also [`getringinfo!`](@ref) and [`getringinfo`](@ref).

# Example

```julia
import Healpix
res = Healpix.Resolution(256)

# Show information about ring #10
print(getringinfo(res, 10))
```
