```
hdf2imas(filename::AbstractString; error_on_missing_coordinates::Bool=true, kw...)
```

OMAS Pythonプラットフォームによって生成されたHDF5ファイルからデータをロードします（すなわち、階層的HDF5）。

`kw...` 引数は `HDF5.h5open` 関数に渡されます。
