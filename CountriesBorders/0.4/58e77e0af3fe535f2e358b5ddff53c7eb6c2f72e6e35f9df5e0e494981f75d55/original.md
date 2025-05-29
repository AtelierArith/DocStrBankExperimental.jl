```
SkipFromAdmin(admin::AbstractString, idxs::AbstractVector{<:Integer})
SkipFromAdmin(admin::AbstractString, idx::Int)
SkipFromAdmin(admin::AbstractString, [::Colon])
```

Structure used to specify parts of countries to skip when generating contours with [`extract_countries`](@ref).

When instantiated with just a country name or with a name and an instance of the `Colon` (`:`), it will signal that the full country whose ADMIN name starts with `admin` (case sensitive) will be removed from the output of `extract_countries`.

If created with an `admin` name and a list of integer indices, the polygons at the provided indices will be removed from the `MultiPolyArea` associated to country `admin` if this is present in the output of `extract_countries`.

## Note

The constructor does not perform any validation to verify that the provided `admin` exists or that the provided `idxs` are valid for indexing into the `MultiPolyArea` associated to the borders of `admin`.
