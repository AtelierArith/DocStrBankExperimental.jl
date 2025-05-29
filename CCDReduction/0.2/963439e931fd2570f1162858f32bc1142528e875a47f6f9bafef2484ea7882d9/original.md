```
filenames(f,
          collection;
          path = nothing,
          save_prefix = nothing,
          save_suffix = nothing,
          save = any(!isnothing, (save_prefix, path, save_suffix)),
          save_delim = "_",
          ext = r"fits(\.tar\.gz)?"i,
          kwargs...)
```

Iterates over the file paths of the collection applying function `f` at each step.

The output from `f` can be saved using the appropriate keyword arguments. The `save_prefix` argument will add a prefix to each filename delimited by `save_delim`. `save_suffix` will add a suffix prior to the extension, which can be manually provided via `ext`, similar to [`fitscollection`](@ref). Files will be saved in the directory they are stored unless `path` is given. Finally, `save` will default to `true` if any of the previous arguments are set, but can be manually overridden (useful for testing). Files will be saved using [`CCDReduction.writefits`](@ref).

# Examples

```julia
collection = fitscollection("~/data/tekdata")
data = map(filenames(collection)) do path
    fh = FITS(path)
    data = getdata(fh[1]) # assuming all 1-hdu are ImageHDUs
    close(fh)
    data
end
```

The above generates `data` which consists of image arrays corresponding to 1st hdu of FITS file paths present in `collection`. For saving the `data` simultaneously with the operations performed

```julia
data = map(filenames(collection; path = "~/data/tekdata", save_prefix = "retrieved_from_filename")) do img
    fh = FITS(path)
    data = getdata(fh[1]) # assuming all 1-hdu are ImageHDUs
    close(fh)
    data
end
```

The retrieved data is saved as `retrieved_from_filename_(original_name)` (FITS files) at `path = "~/data/tekdata"` as specified by the user.
