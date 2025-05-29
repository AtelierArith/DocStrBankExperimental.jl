```
map_get_gxf(map_gxf::String)
```

Use ArchGDAL to read in map data from GXF file.

**Arguments:**

  * `map_gxf`: path/name of map GXF file (`.gxf` extension optional)

**Returns:**

  * `map_map`: `ny` x `nx` 2D gridded map data
  * `map_xx`:  `nx` map x-direction (longitude) coordinates
  * `map_yy`:  `ny` map y-direction (latitude)  coordinates
