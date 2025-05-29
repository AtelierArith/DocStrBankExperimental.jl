```
sph2cut(sphfile::AbstractString; theta, phi, ipol) -> cut::Cut

sph2cut(sph:SPHQPartition; theta, phi, ipol) -> cut::Cut

sph2cut(sphs:Vector{SPHQPartition}; theta, phi, ipol) -> cuts::Vector{Cut}
```

Convert a set of Q-type spherical wave modal coefficients to far-field electric field  values, returned as a `Cut` object. 

The single positional input argument can be either a string containing the name  of a Ticra-compatible Q-type spherical wave file, or the returned value from reading  such a file with `read_sphfile`.

## Optional Keyword Arguments:

  * `theta`: An abstract range denoting the desired polar angles (colattitudes)  in degrees at which the field should be evaluated. If an empty range is provided (the default), then the values will be determined automatically by examining the modal content in `sph`.
  * `phi`: An abstract range denoting the desired azimuthal angles in degrees at  which the field should be evaluated.  If an empty range is provided (the default), then the values will be determined automatically by examining the modal content in `sph`.
  * `ipol`:  An integer in the range 0:3 denoting the desired polarization decomposition  for the computed field values. The meanings of these values are:

      * 0: (Default value) Choose the basis among choices 2 or 3 that produces the largest peak copol magnitude.
      * 1: Use a (θ̂, ϕ̂) basis.
      * 2: Use a (R̂, L̂) (i.e., circular polarization) basis.
      * 3: Use a (ĥ, v̂) (Ludwig 3) basis.

## Usage Example

```
cut = sph2cut("testfile.sph"; phi=0:5:355, theta=0:1:180, ipol=2)
```
