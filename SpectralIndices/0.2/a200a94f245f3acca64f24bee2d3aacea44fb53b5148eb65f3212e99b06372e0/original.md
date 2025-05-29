```
SpectralIndex(index::Dict{String, Any})
```

This object allows interaction with specific Spectral Indices in the Awesome Spectral Indices list. Attributes of the Spectral Index can be accessed and the index itself can be computed.

# Arguments

  * `index::Dict{String, Any}`: A dictionary with the following keys:

      * `"short_name"`: Short name of the spectral index.
      * `"long_name"`: Long name or description of the spectral index.
      * `"bands"`: List of bands or wavelengths used in the index calculation.
      * `"application_domain"`: Application domain or use case of the spectral index.
      * `"reference"`: Reference or source of the spectral index formula.
      * `"formula"`: Mathematical formula of the spectral index.
      * `"date_of_addition"`: Date when the spectral index was added (in "yyyy-mm-dd" format).
      * `"contributor"`: Contributor or source of the spectral index information.
      * `"platforms"`: Platforms or sensors for which the index is applicable.

# Returns

A `SpectralIndex` object containing the specified index information.

# Examples

```julia-repl
julia> indices["NIRv"]

```

Or, accessing directly the provided Dict of spectral indices:

```julia-repl
NIRv
```
