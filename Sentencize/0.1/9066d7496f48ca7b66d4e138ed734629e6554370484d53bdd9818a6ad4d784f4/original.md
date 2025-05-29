Prefixes(prefixes::Dict{T,PrefixType}=Dict{String,PrefixType}(); prefix_file::Union{String,Nothing}=nothing, lang::Union{String,Nothing}="en") where {T<:AbstractString}

Constructs `Prefixes`.

# Arguments

  * `prefixes::Dict{<:AbstractString,PrefixType}=Dict{T,PrefixType}()`: Optional. A dictionary of non-breaking prefixes.
  * `prefix_file::Union{String,Nothing}=nothing`: Optional. A path to a file containing non-breaking prefixes to add to provided `prefixes`.
  * `lang::AbstractString="en"`: Optional. The language of the non-breaking prefixes (see `?SUPPORTED_LANG` for available languages) to be added to `prefixes`.
