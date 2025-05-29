```
data_colors(
    data::AbstractMatrix{<:Real};
    run_umap::Bool = true,
    minimal_saturation::Real = 33,
    minimal_lightness::Real = 20,
    maximal_lightness::Real = 80
)::AbstractVector{<:AbstractString}

data_colors(
    data::AbstractMatrix{<:Real};
    run_umap::Bool = true,
    groups::Union{AbstractVector{T}},
    minimal_saturation::Real = 33,
    minimal_lightness::Real = 20,
    maximal_lightness::Real = 80
)::Dict{T, <:AbstractString}
```

Compute colors for multi-dimensional data.

Given a matrix of observation/element columns and variable/measurement rows, compute a color for each column (or group of columns) such that the colors are distinct, and where more-similar colors roughly designate more-similar data columns (or groups of columns).

This is intended to provide a "reasonable" set of colors to "arbitrary" data, for use as a convenient default when investigating unknown data sets. It is not meant to replace hand-picked colors tailored for specific data (e.g., using red colors for "bad" columns and green colors for "good" columns).

This ensures all colors are distinct by packing the (visible part) of the CIELAB color space with the needed number of spheres using [`distinct_colors`](@ref). To assign the colors to the data, it uses UMAP to reduce the data to 3D. It then uses principal component analysis to represent both the chosen colors (3D sphere centers) and the (3D UMAP) data as point clouds with coordinates in the range 0-1, and finally uses a stable matching algorithm to map these point clouds to each other, thereby assigning a color to each data column. If the data is grouped, then the center of gravity of each group is used to generate a color for each group.

# Arguments

  * `data`: A matrix whose columns represent elements/observations and columns represent variables/measurements.
  * `run_umap`: A Boolean specifying whether to run UMAP on the data to convert it to 3D. If `false`, the data matrix must have exactly 3 columns and will be used as-is.
  * `groups`: An optional array with an entry per column containing the identifier of the group the column belongs to.
  * `minimal_saturation`: Exclude colors whose saturation (hypot(a, b) in CIELAB color space) is less than this value.
  * `minimal_lightness`: Exclude colors whose lightness (l in CIELAB color space) is less than this value.
  * `maximal_lightness`: Exclude colors whose lightness (l in CIELAB color space) is more than this value.

# Returns

If `groups` was specified, an dictionary mapping the group names to colors. Otherwise, a vector with one entry per column containing its color. Colors are named in the usual `#RRGGBB` hexadecimal format.

!!! note
    Since this calls UMAP, which (sometimes) uses randomness under the hood, and doesn't have a way to pass it a random number generator, then if you want reproducible results, you need to call `Random.seed!(...)` yourself immediately before calling `data_colors`. If/when UMAP allows passing the random number generator as a parameter (as it should), then we should add the same parameter here and pass it to UMAP.

