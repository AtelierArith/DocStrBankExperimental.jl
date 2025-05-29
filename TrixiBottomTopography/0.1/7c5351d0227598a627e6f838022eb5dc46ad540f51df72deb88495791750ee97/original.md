```
convert_dgm_2d(path_read::String, path_write::String; excerpt = 1)
```

Function to convert [DGM](https://www.opengeodata.nrw.de/produkte/geobasis/hm/dgm1_xyz/dgm1_xyz/) data files into two dimensional readable files.

Inputs:

  * `path_read`: String of the path of the DGM data which should be converted
  * `path_write`: String of the path where the new file should be saved.             (Needs to also include the name of the file)
  * `excerpt`: Optional integer that specifies a stride through of the data that will be extracted. E.g.          if excerpt is set to 10, only every 10th `x` and `y` value are considered with their          corresponding `z` values. The default value is 1 which means that every value is taken.
