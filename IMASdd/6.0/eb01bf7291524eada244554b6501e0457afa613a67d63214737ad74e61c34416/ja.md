```
h5i2imas(filename::AbstractString, @nospecialize(ids::IDS)=dd(); kw...)
```

IMASプラットフォーム（すなわち、テンソル化されたHDF5）によって生成されたHDF5ファイルからデータをロードします。

`kw...` 引数は `HDF5.h5open` 関数に渡されます。
