```
BondTable(bondarray; description, collapsed)
```

Take as input an array of bonds and creates a floating table that show all the bonds in the input array. 

If `description` is not provided, it defaults to the text *BondTable*. Description can be either a string or a HTML output.

The optional `collapsed` kwarg can be used to specify whether the BondTable should stay collapsed or not when shown. If not provided, the BondTable will *not* be collapsed.

The *collapsed* status of the BondTable is persistent across reactive runs of the cell showing the BondTable.

See also: [`StructBond`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fieldbond`](@ref), [`@fielddescription`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
