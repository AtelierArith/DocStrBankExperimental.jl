```
coord, Data_3D_Arrays, Name_Vec = read_data_VTR(fname)
```

Reads a VTR (structured grid) VTK file `fname` and extracts the coordinates, data arrays and names of the data. In general, this only contains a piece of the data, and one should open a `*.pvtr` file to retrieve the full data
