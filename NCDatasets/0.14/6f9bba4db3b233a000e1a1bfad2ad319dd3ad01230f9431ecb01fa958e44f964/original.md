```
ncgen(fname; ...)
ncgen(fname,jlname; ...)
```

Generate the Julia code that would produce a NetCDF file with the same metadata as the NetCDF file `fname`. The code is placed in the file `jlname` or printed to the standard output. By default the new NetCDF file is called `filename.nc`. This can be changed with the optional parameter `newfname`.
