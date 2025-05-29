```
get_path()
```

Get the path of a given asset type.

# Arguments

  * `asset_type::Symbol`: The type of asset, possible values are `:examples`, `:addons`, and `:templates`.

# Returns

  * `String`: The path of the folder containing all assets of the given type.

# Example

```julia
get_path(:examples)
```
