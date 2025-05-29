```
convert_dgm_1d(path_read::String, path_write::String; excerpt = 1, direction = "x", section = 1)
```

Function to convert [DGM](https://www.opengeodata.nrw.de/produkte/geobasis/hm/dgm1_xyz/dgm1_xyz/) data files into one dimensional readable files.

Inputs:

  * `path_read`: String of the path of the DGM data which should be converted
  * `path_write`: String of the path where the new file should be saved.             (Needs to also include the name of the file)
  * `excerpt`: Optional integer that specifies a stride through of the data that will be extracted. E.g.          if excerpt is set to 10, only every 10th `x` and `y` value are considered with their          corresponding `z` values. The default value is 1 which means that every value is taken.
  * `direction`: Optional String that specifies if the one dimensional data should be read from the            `x` or `y` direction. By default this is set to the `x` direction.
  * `section`: Optional integer which can be between 1 and 1000 and specifies which section of the          other dimension should be chosen. By default this values is set to 1 which means          that if direction is set to `x`, the corresponding `z` values are taken with respect to the          first `y` value.
