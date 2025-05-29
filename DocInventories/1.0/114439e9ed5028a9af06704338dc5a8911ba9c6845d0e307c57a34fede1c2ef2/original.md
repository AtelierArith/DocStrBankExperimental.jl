An inventory of link targets in a project documentation.

```julia
inventory = Inventory(
    source;
    mime=auto_mime(source),
    root_url=root_url(source)
)
```

loads an inventory file from the given `source`, which can be a URL or the path to a local file. If it is a URL, the options `timeout` (seconds to wait for network connections), `retries` (number of times to retry) and `wait_time` (seconds longer to wait between each retry) may be given. The `source` must contain data in the given mime type. By default, the mime type is derived from the file extension, via [`auto_mime`](@ref).

The `Inventory` acts as a collection of [`InventoryItems`](@ref InventoryItem), representing all the objects, sections, or other linkable items in the online documentation of a project.

Alternatively,

```julia
inventory = Inventory(; project, version="", root_url="", items=[])
```

with a mandatory `project` argument instantiates an `inventory` with the [`InventoryItems`](@ref InventoryItem) in `items`. If `items` is not given, the resulting empty `inventory` can have [`InventoryItems`](@ref InventoryItem) added afterwards via [`push!`](@extref Julia Base.push!).

# Attributes

  * `project`: The name of the project
  * `version`: The version of the project (e.g., `"1.0.0"`)
  * `root_url`: The root URL to which the `item.uri` of any [`InventoryItem`](@ref) is relative. If not empty, should start with `"https://"` and end with a slash.
  * `source`: The URL or filename from which the inventory was loaded.
  * `sorted`: A boolean to indicate whether the items are sorted by their `name`  attribute, allowing for efficient lookup. This is `true` for all inventories  loaded from a URL or file and `false` for manually instantiated inventories.

Note that `source` and `sorted` are informational attributes only and are ignored when comparing two `Inventory` objects.

# Item access

Items can be accessed via iteration (`for item in inventory`), by numeric index (`inventory[1]`, `inventory[2]`, … `inventory[end]`), or by lookup: `inventory[name]` or `inventory[spec]`, where `spec` is a string of the form ```":[domain:]role:`name`"```, see the discussion of `spec` in [`InventoryItem`](@ref). The lookup delegates to [`find_in_inventory`](@ref) with `quiet=true` and takes into account [`item.priority`](@ref InventoryItem).

# Search

The inventory can be searched by calling `inventory(search; include_hidden_priority=true)`. This returns a list of all items that contain `search` in `spec(item)` or `repr(item; context=(:full => true))`. Typically, `search` would be a string or a [`Regex`](@extref Julia man-regex-literals). Some examples for common searches:

  * A `spec` of the form ```":domain:role:`name`"```, in full, partially, or as a regex.
  * Part of a url of a page in the project's documentation, as a string
  * The title of a section as it appears somewhere in the project's documentation.

The search results are sorted by [`abs(item.priority)`](@ref InventoryItem). If `include_hidden_priority=false`, negative `item.priority` values are omitted.

# Methods

  * [`find_in_inventory(inventory, name)`](@ref find_in_inventory) – find a single item in the `inventory`
  * [`save(filename, inventory; mime=auto_mime(filename))`](@ref save) – write the `inventory` to a file in any supported output format.
  * [`show_full(inventory)`](@ref) – show the unabbreviated inventory in the REPL (ideally via [`TerminalPager`](https://ronisbr.github.io/TerminalPager.jl/))
  * [`uri(inventory, key)`](@ref uri(::Inventory, key)) – obtain the full URI for an item from the `inventory`.
  * [`push!(inventory, items...)`](@extref Julia Base.push!) – add [`InventoryItems`](@ref InventoryItem) to an existing `inventory`.
  * [`append!(inventory, collections...)`](@extref Julia Base.append!) – add collections of [`InventoryItems`](@ref InventoryItem) to an existing `inventory`.
  * [`collect(inventory)`](@extref Julia Base.collect-Tuple{Any}) – convert the inventory to a standard `Vector` of [`InventoryItems`](@ref InventoryItem).
  * [`set_metadata(inventory)`](@ref) – Modify the `project` and `version` metadata.
  * [`sort(inventory)`](@extref Julia Base.sort) – convert an unsorted inventory into a sorted one.
