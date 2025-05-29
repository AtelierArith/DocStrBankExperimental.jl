```
fld_write(file, data ; kwargs...)
```

Write data into AVS format `.fld` file. See README for file format.

in

  * `file` name of file typically ending in `.fld`
  * `data` real data array

option

  * `check::Bool`         report error if file exists; default `true`
  * `dir::String`         directory name to prepend file name; default `""`
  * `endian::`Symbol``:le`little endian (default),`:be` big endian
  * `head::Array{String}` comment information for file header
  * `raw::Bool`           put raw data in `name.raw`, header in `name.fld`                       where `file` = `name.fld`; default `false`
