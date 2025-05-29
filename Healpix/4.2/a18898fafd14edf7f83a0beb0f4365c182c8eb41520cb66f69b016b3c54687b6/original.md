```
struct HealpixMap{T, O <: Order, AA <: AbstractArray{T, 1}} <: AbstractHealpixMap{T}
```

A Healpix map. The type `T` is used for the value of the pixels in a map, and it can be anything (even a string!). The type `O` is used to specify the ordering of the pixels, and it can either be `RingOrder` or `NestedOrder`. The type `AA` is used to store the array of pixels; typical types are `Vector`, `CUArray`, `SharedArray`, etc.

A `HealpixMap` type contains the following fields:

  * `pixels`: array of pixels
  * `resolution`: instance of a `Resolution` object

You can construct a map using one of the following forms:

  * `HealpixMap{T, O, AA}(arr)` and `HealpixMap{T, O, AA}(nside::Number)` will use `AA` as basetype
  * `HealpixMap{T, O}(arr)` and `HealpixMap{T, O}(nside::Number)` will use `Array{T, 1}` as basetype

# Examples

The following example creates a map with `NSIDE=32` in `RING` order, containing integer values starting from 1:

```
mymap = Healpix.HealpixMap{Int64, Healpix.RingOrder}(1:Healpix.nside2npix(32))
```

The call to `collect` is required to convert the range in an array.

This example creates a map in `NESTED` order, with `NSIDE=64`, filled with zeroes:

```
mymap = Healpix.HealpixMap{Float64, Healpix.NestedOrder}(64)
```

Finally, the following examples show how to use `SharedArray`:

```
using SharedArrays

# Create a map with all pixels set to zero
mymap = Healpix.HealpixMap{Float64, Healpix.NestedOrder, SharedArray{Float64, 1}}(64)

# Create a map and initialize pixel values with a SharedArray
pixels = SharedArray{Int64, 1}(1:12 |> collect)
mymap = Healpix.HealpixMap{Int64, Healpix.RingOrder, SharedArray{Int64, 1}}(m)
```
