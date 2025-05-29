```
PVTKFile
```

Hold all relevant information about a Parallel VTK XML file that has been read in.

# Fields

  * `filename`: original path to the PVTK file that has been read in
  * `xml_file`: xml info
  * `file_type`: currently only `"PRectilinearGrid"` or `"PImageData"` are supported
  * `version`: VTK XML file format version
  * `vtk_filenames`: vector with strings that contain the filenames of each of the parallel files
  * `vtk_files`: vector with `VTKFile` data that contains the info about each of the files
