```
read_mtg(file, attr_type = Dict, mtg_type = MutableNodeMTG; sheet_name = nothing)
```

Read an MTG file

# Arguments

  * `file::String`: The path to the MTG file.
  * `attr_type::DataType = Dict`: the type used to hold the attribute values for each node.
  * `mtg_type = MutableNodeMTG`: the type used to hold the mtg encoding for each node (*i.e.*

link, symbol, index, scale). See details section below.

  * `sheet_name = nothing`: the sheet name in case you're reading an `xlsx` or `xlsm` file. It

reads the first sheet if `nothing` (default behavior).

# Details

`attr_type` should be:

  * `NamedTuple` if you don't plan to modify the attributes of the mtg, *e.g.* to use them for

plotting or computing statistics...

  * `MutableNamedTuple` if you plan to modify the attributes values but not adding new attributes

very often, *e.g.* recompute an attribute value...

  * `Dict` or similar (*e.g.* `OrderedDict`) if you plan to heavily modify the attributes, *e.g.*

adding/removing attributes a lot

The `MultiScaleTreeGraph` package provides two types for `mtg_type`, one immutable ([`NodeMTG`](@ref)), and one mutable ([`MutableNodeMTG`](@ref)). If you're planning on modifying the mtg encoding of some of your nodes, you should use [`MutableNodeMTG`](@ref), and if you don't want to modify anything, use [`NodeMTG`](@ref) instead as it should be faster.

# Note

See the documentation of the MTG format from the package documentation for further details, *e.g.* [The MTG concept](@ref).

# Returns

The MTG root node.

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# Or using another `MutableNamedTuple` for the attributes to be able to add one if needed:
mtg = read_mtg(file,Dict);

# We can also read an mtg directly from an excel file from the field:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","tree3h.xlsx")
mtg = read_mtg(file)
```
