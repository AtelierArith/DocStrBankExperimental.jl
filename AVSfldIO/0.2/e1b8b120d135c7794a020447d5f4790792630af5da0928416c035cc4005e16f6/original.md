```
data = fld_read(file::String ; dir::String="", chat=false)
```

Read data from AVS format `.fld` file

in

  * `file` file name, usually ending in `.fld`

option

  * `dir::String` prepend file name with this directory; default ""
  * `chat::Bool` verbose?

out

  * `data` Array (1D - 5D) in the data type of the file itself
