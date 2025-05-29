```
fitscollection(dir;
               recursive=true,
               abspath=true,
               keepext=true,
               ext=r"fits(\.tar\.gz)?",
               exclude=nothing,
               exclude_dir=nothing,
               exclude_key=("", "HISTORY"))
```

Walk through `dir` collecting FITS files, scanning their headers, and culminating into a `DataFrame` that can be used with the generators for iterating over many files and processing them. If `recursive` is false, no subdirectories will be walked through.

The table returned will contain the path to the file, the name of the file, and index of the corresponding HDU, and each FITS header column and value. If two FITS files have distinct columns, they will both appear in the table with `missing` in the appropriate rows.

!!! note "Duplicate Keys"
    In certain cases, there are multiple FITS headers with the same key, e.g., `COMMENT`. In these cases, only the first instance of the key-value pair will be stored.


If `abspath` is true, the path in the table will be absolute. If `keepext` is true, the name in the table will include the file extension, given by `ext`. `ext` will be used with `endswith` to filter for fits files compatible with `FITSIO.FITS`. `exclude` is a pattern that can be used with `occursin` to exclude certain filenames. For example, to exclude any files containing "sky",

```julia
fitscollection(...; exclude="sky")
```

to exclude exact filenames, [regex strings](https://docs.julialang.org/en/v1/manual/strings/#Regular-Expressions-1) will prove powerful

```julia
fitscollection(...; exclude=r"^tek001\d")
```

finally, using external tools like [Glob.jl](https://github.com/vtjnash/Glob.jl) allows further customization

```julia
using Glob
fitscollection(...; exclude=fn"tek001*.fits") # same as regex match above
```

Similarly, `exclude_dir` allows excluding entire folders using pattern matching (e.g. skipping a backup folder `exclude_dir="backup"`). `exclude_key` allows excluding certain entries in the header unit of `ImageHDU` in FITS files (e.g. skipping `"HISTORY"` and `""` `exclude_key = ("HISTORY", "")`).

For more information about the file matching and path deconstruction, see the extended help (`??fitscollection`)

# Extended Help

## Parts of a path

Let's look at some file paths starting from `"/data"`. Here are examples of how they would be parsed

```plain
 root  dir   base   ext
[----][---][------][---]
/data/test/tek0001.fits

 root    dir     base   ext
[----][-------][------][---]
/data/test/sci/tek0001.fits
```

If `keepext` is `true`, `name=base * ext`, otherwise it is just `base`. If `abspath` is `true`, the path will be `root * dir * base * ext`, otherwise it will be `dir * base * ext`. These options allow flexility in creating a table that can be easily saved and loaded to avoid having to manually filter files. Especially consider how `abspath` can allow keeping tables that will transfer easily between computers or between data sources with common structures.
