```
(dat, rdb_hdr) = loadpfile(fid::IOStream ; ...)
```

Load data for one or more echoes from GE MRI scan Pfile.

in

  * `fid::IOStream`

option

  * `coils::AbstractVector{Int}`

only get data for these coils; default: all coils

  * `echoes::AbstractVector{Int}`

only get data for these echoes; default: all echoes

  * `slices::AbstractVector{Int}`

only get data for these slices; default: `2:nslices` (NB!)  because first slice (dabslice=0 slot) may contain corrupt data.

  * `views::AbstractVector{Int}`

only get data for these views; default: all views

  * `quiet::Bool` non-verbosity, default `false`

out

  * `dat::Array{Complex{Int16}}` `[ndat, ncoil, nslice, necho, nview]`
  * `rdb_hdr::NamedTuple` header information

To save memory the output type is complex-valued Int16.
