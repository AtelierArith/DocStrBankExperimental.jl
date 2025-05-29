```
head, is_external_file, fid = fld_open(file ; dir::String="", chat=false)
```

Read header data from AVS format `.fld` file. Leaves file open for more reading.

in

  * `file::String` file name, usually ending in `.fld`

option

  * `dir::String` prepend file name with this directory; default ""
  * `chat::Bool` verbose? default: `false`

out

  * `head::String` array of header information
  * `is_external_file::Bool` true if AVS external format
  * `fid::IOstream`
