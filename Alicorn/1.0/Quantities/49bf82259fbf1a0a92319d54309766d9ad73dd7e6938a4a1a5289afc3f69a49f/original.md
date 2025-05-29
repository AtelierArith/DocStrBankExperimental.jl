```
SimpleQuantity(quantity::AbstractQuantity)
```

Construct a `SimpleQuantity` from a physical quantity of any implementation of `AbstractQuantity`.

If `quantity` is of type `SimpleQuantity`, it is returned unchanged. If `quantity` is of type `Quantity`, it is expressed in terms of the SI units specified by `quantity.InternalUnits`.

# Example

```jldoctest
julia> ucat = UnitCatalogue() ; intu = InternalUnits(length=2*ucat.milli*ucat.meter) ;

julia> q = Quantity(4, Dimension(L=1), intu)
Quantity{Int64} of dimension L^1 in units of (2 mm):
 4
julia> sq = SimpleQuantity(q)
8 mm
```
