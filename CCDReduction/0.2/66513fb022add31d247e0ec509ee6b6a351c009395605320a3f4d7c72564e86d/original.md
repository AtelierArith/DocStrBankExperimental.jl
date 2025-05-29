```
arrays(f,
       collection;
       path = nothing,
       save_prefix = nothing,
       save_suffix = nothing,
       save = any(!isnothing, (save_prefix, path, save_suffix)),
       save_delim = "_",
       ext = r"fits(\.tar\.gz)?"i,
       kwargs...)
```

Iterates over the image arrays of the collection applying function `f` at each step.

The output from `f` can be saved using the appropriate keyword arguments. The `save_prefix` argument will add a prefix to each filename delimited by `save_delim`. `save_suffix` will add a suffix prior to the extension, which can be manually provided via `ext`, similar to [`fitscollection`](@ref). Files will be saved in the directory they are stored unless `path` is given. Finally, `save` will default to `true` if any of the previous arguments are set, but can be manually overridden (useful for testing). Files will be saved using [`CCDReduction.writefits`](@ref).

# Examples

```julia
collection = fitscollection("~/data/tekdata")
processed_images = map(arrays(collection)) do arr
    trim(arr, (:, 1040:1059))
end
```

The above generates `processed_images` which consists of trimmed versions of image arrays present in `collection`. For saving the `processed_images` simultaneously with the operations performed

```julia
processed_images = map(arrays(collection; path = "~/data/tekdata", save_prefix = "trimmed")) do img
    trim(img, (:, 1040:1059))
end
```

The trimmed image arrays are saved as `trimmed_(original_name)` (FITS files) at `path = "~/data/tekdata"` as specified by the user.
