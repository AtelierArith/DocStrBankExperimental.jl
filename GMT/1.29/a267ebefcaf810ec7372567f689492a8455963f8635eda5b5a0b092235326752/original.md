I = mosaic(; region=??, ...)

Same as above but this time the BoundingBox is extracted from the `region` option. Note that this option is the same as in, for example, the `coast` module.

# Example

```jldoctest
julia> I = mosaic(region=(91,110,6,22))		# zoom level is computed automatically
viz(I, coast=true)
```
