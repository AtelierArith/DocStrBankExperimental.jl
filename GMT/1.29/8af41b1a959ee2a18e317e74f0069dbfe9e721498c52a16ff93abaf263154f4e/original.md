I = mosaic(address::String; ...)

Same as above but the `lon` & `lat` are extracted from the `address` code. The code can be a $quadtree$ or a $XYZ$ tile address. This is a more specialized usage that relies on users knowledge on tile code names based on quadtrees or XYZ encoding. An example of these codes is provided by the attributes of when we use the `mesh=true` option.

An important difference between the `address` option and the `lon & lat` option is that the `address` option also set the zoom level, so here the $zoom$ option means the extra zoom level added to that implied by $address$. A number higher than 3 is suspiciously large.

# Example

```jldoctest
julia> I = mosaic("033110322", zoom=2)
viz(I, coast=true)
```
