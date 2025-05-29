```
function read_tb_crys(filename, tbc::tb_crys)
```

Reads and returns from `filename` a `tb_crys` object. See `write_tb_crys`

If cannot find `"filename"`, will look for `"filename.xml"`, `"filename.gz"`, `"filename.xml.gz"`

Can read gzipped files directly.
