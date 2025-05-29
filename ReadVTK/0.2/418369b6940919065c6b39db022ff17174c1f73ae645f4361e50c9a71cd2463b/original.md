```
PVDFile
```

Hold all relevant information about a PVD file that has been read in.

# Fields

  * `filename`: original path to the PVTK file that has been read in
  * `file_type`: currently only `"PRectilinearGrid"` or `"PImageData"` are supported
  * `vtk_filenames`: vector with strings that contain the filenames of each of the files
  * `directories`: vector with strings that contain the directories where each of the files are
  * `timestep`: vector with `Float64` that contains the time of each of the files
