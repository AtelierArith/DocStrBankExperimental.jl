```
loadrxnetwork(ft::BNGNetwork, rxfilename; name = gensym(:ReactionSystem), verbose = false, kwargs...)
```

Parses a BioNetGen `.net` file and constructs a `ParsedReactionNetwork` object.

# Arguments

  * `ft::BNGNetwork`: Indicates the file to be parsed is a BioNetGen ".net" file.
  * `rxfilename::String`: Path to the `.net` file to be parsed.
  * `name::Symbol`: (Optional) Name for the resulting `ReactionSystem`. Defaults to a generated symbol.
  * `verbose::Bool`: (Optional) If `true`, prints detailed progress information during parsing. Defaults to `true`.
  * `kwargs...`: Additional keyword arguments passed to the `ReactionSystem` constructor.

# Returns

A `ParsedReactionNetwork` object containing:

  * The `ReactionSystem` with reactions, species, and parameters.
  * Initial conditions (`u0`) and parameter values (`p`).
  * Mappings between variable names and symbols.

# Notes

This function parses a subset of the BioNetGen `.net` file format. It assumes:

  * Expressions are compatible with Julia syntax.
  * Time-dependent or conditional logic is not supported.
  * More complicated functional constructs may not be supported.

# Example

```julia
parsed_network = loadrxnetwork(BNGNetwork(), "path/to/network.net", verbose = true)
```
