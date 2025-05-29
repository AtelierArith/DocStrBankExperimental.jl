An item inside an [`Inventory`](@ref).

```julia
item = InventoryItem(; name, role, uri, priority=1, domain="jl", dispname="-")
```

represents a linkable item inside a project documentation, referenced by `name`. The `domain` and `role` take their semantics from the [Sphinx project](@extref sphinx usage/domains/index), see *Attributes* for details on these parameters, as well as `priority` and `dispname`. The `uri` is relative to a project root, which should be the [`Inventory.root_url`](@ref Inventory) of the `inventory` containing the `InventoryItem`.

For convenience, an `InventoryItem` can also be instantiated from a mapping `spec => uri`, where ```spec=":domain:role:`name`"``` borrows from Sphinx' [cross-referencing syntax](@extref sphinx usage/referencing):

```julia
item = InventoryItem(
    ":domain:role:`name`" => uri;
    dispname=<name>,
    priority=(<domain == "std" ? -1 : 1>)
)
```

The `domain` is optional: if ```spec=":role:`name`"```, the `domain` is `"std"` for `role="label"` or `role="doc"`, and `"jl"` otherwise. The `role` is mandatory for code objects. For non-code objects,

```julia
item = InventoryItem(
    "title" => uri;
    dispname=<title>,
    priority=-1
)
```

indicates a link to a section header in the documentation of a project. The `name` will be a sluggified version of the title, making the `item` equivalent to ```item = InventoryItem(":std:label:`name`" => uri; dispname=title, priority=-1)```.

# Attributes

  * `name`: The object name for referencing. For code objects, this should be the  fully qualified name. For section names, it may be a slugified  version of the section title. It must have non-zero length.
  * `domain`: The name of a [Sphinx domain](@extref sphinx usage/domains/index).  Should be `"jl"` for Julia code objects (default), `"py"` for Python code  objects, and `"std"` for text objects such as section names. Must have  non-zero length, and must not contain whitespace or a colon.
  * `role`: A domain-specific [role](@extref sphinx :term:`role`) ([type](@extref sphinx sphinx.domains.ObjType)). Must have nonzero length and not contain whitespace.
  * `priority`: An integer flag for placement in search results. Used when searching in an [`Inventory`](@ref), for item access in an [`Inventory`](@ref), and with [`find_in_inventory`](@ref). The following flag values are supported:

      * `1`: the "default" priority. Used by default for all objects not in the `"std"` domain (that is, all "code" objects such as those in the `"jl"` domain).
      * `0`: object is important
      * `2` (or higher): object is unimportant
      * `-1` (or lower): object is "hidden" (may be omitted from search). Used by default for all objects in the `std` domain (section titles)

    See [`find_in_inventory`](@ref) for details. The above semantics match those used by [Sphinx](https://github.com/sphinx-doc/sphinx/blob/2f60b44999d7e610d932529784f082fc1c6af989/sphinx/domains/__init__.py#L370-L381).
  * `uri`: A URI for the location of the object's documentation, relative to the location of the inventory file containing the `item`. Must not contain whitespace. May end with `"$"` to indicate a placeholder for `name` (usually as `"#$"`, for an HTML anchor matching `name`).
  * `dispname`: A full plain text representation of the object. May be `"-"` if the display name is identical to `name` (which it should be for code objects). For section titles, this should be the plain text of the title, without formatting, but not slugified.

# Methods

  * [`uri`](@ref) – Extract the full URI, resolving the `$` placeholder and prepending a `root_url`, if applicable.
  * [`dispname`](@ref) – Extract the `dispname`, resolving the "-" shorthand, if applicable.
  * [`spec`](@ref) – Return the specification string ```":domain:role:`name`"``` associated with the item
