```
head = fld_header(file::String ; dir::String="", chat=false)
```

Read header data from AVS format `.fld` file, then close file.

in

  * `file::String` file name, usually ending in `.fld`

option

  * `dir::String` prepend file name with this directory; default ""
  * `chat::Bool` verbose? default: `false`

out

  * `head::String` array of header information
