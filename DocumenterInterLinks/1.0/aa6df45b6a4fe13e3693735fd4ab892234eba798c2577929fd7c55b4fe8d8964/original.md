Plugin for enabling external links in `Documenter.jl.`

```julia
links = InterLinks(
    mappings...;
    default_inventory_file="objects.inv",
    alias_methods_as_function=true,
)
```

instantiates a plugin object that must be passed as an element of the `plugins` keyword argument to [`Documenter.makedocs`](@extref). This then enables `@extref` links in the project's documentation to be resolved, see the [Syntax](@ref) documentation for details. The `mappings` connect project names to project root URLs and inventories, e.g.,

```julia
links = InterLinks(
    "Julia" => (
        "https://docs.julialang.org/en/v1/",
        "https://docs.julialang.org/en/v1/objects.inv",
        joinpath(@__DIR__, "inventories", "Julia.toml")
    ),
    "Documenter" => "https://documenter.juliadocs.org/stable/objects.inv",
    "sphinx" => "https://www.sphinx-doc.org/en/master/";
)
```

See the details below.

# Arguments

The `InterLinks` plugin receives mappings of project names to the project root URL and inventory locations. Each project names must be an alphanumerical ASCII string. For Julia projects, it should be the name of the package without the `.jl` suffix, e.g., `"Documenter"` for [Documenter.jl](https://documenter.juliadocs.org/). For Python projects, it should be the name of project's main module.

The root url / inventory location (the value of the mapping), can be given in any of the following forms (from most common to least common):

  * A single string with a project root URL, e.g., the `"sphinx"` entry in the above example. The URL must end with a slash. This looks for the inventory file with the name corresponding to `default_inventory_file` directly underneath the given root URL. This is the most common form.
  * A tuple of strings, where the first element is the project root URL and all subsequent elements are locations (URLs or local file paths) to an inventory file. The first reachable inventory file will be used. This enables, e.g., to define a local inventory file as a fallback in case the online inventory file location is unreachable, as in the `"Julia"` entry in the above example.
  * A single string with a URL of the inventory file, e.g., the `"Documenter"` entry in the above example. The root URL relative to which all URIs inside the inventory are taken is everything up to the final slash in the inventory URL, `"https://documenter.juliadocs.org/stable/"` in this case. Note that the string has to be a URL, not a local file path, as a file path contains no implicit information about a project's root URL.
  * A [`DocInventories.Inventory`](@extref) instance. This may be useful for using a dynamically constructed inventory.

# Keyword arguments

The keyword arguments to `InterLinks` are experimental and may change in minor versions.

  * `default_inventory_file`: The file name for the inventory file to use if the "inventory location" is given as the root URL. Since both Sphinx and Documenter automatically write `objects.inv`, there is little conceivable reason to set this to something other than the default `"objects.inv"`.
  * `alias_methods_as_function`: If `true` (default), for any inventory loaded from a file or URL, automatically add a `:jl:function:` alias for any `:jl:method` if that alias is unambiguous. This accounts for Documenter preferentially generating method-docstrings from `@autodoc` blocks, even if that method is the only method for the underlying function. For example, the [`Documenter.Selectors.dispatch`](@extref) function only has a method-docstring that would have to be referenced as the excessively long

    ```
    [`Documenter.Selectors.dispatch`](@extref `Documenter.Selectors.dispatch-Union{Tuple{T}, Tuple{Type{T}, Vararg{Any}}} where T<:Documenter.Selectors.AbstractSelector`)
    ```

    With the alias, this can be shortened to ```[`Documenter.Selectors.dispatch`](@extref)```. No alias will be created if there are docstrings for multiple methods of the same function, or if there is an existing function docstring.

# Properties

  * `names`: A list of project names
  * `inventories`: A dictionary of project names to [`DocInventories.Inventory`](@extref) instances
  * `rx`: a [`Regex`](@extref Julia Base.Regex) that matches any valid `@extref` expression that can be resolved.

The `InterLinks` object also acts as a (read-only) ordered dictionary so that, e.g., `links["project1"]` returns the [`DocInventories.Inventory`](@extref) for that project.

# Search

Free-form search in a particular inventory is possible with, e.g.,

```julia
links["Julia"](search)
```

See the discussion on search in the [`DocInventories.Inventory`](@extref) documentation. Such a search returns a list of matching [`DocInventories.InventoryItem`](@extref) instances.

In addition,

```
links(search)
```

allows to search across *all* inventories. This returns a list of `@extref` strings that could be used to reference the matching items.

# Methods

  * [`find_in_interlinks(links, extref)`](@ref) – find the URL for an `extref`

# See also

The `InterLinks` mapping is deliberately reminiscent of the [`intersphinx_mapping`](@extref sphinx) setting in [Sphinx](@extref sphinx :doc:`index`).
