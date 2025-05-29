```
 convertIDLtoVTK(filename; gridType=1, verbose=false)
```

Convert 3D BATSRUS *.out to VTK. If `filename` does not end with "out", it tries to find the ".info" and ".tree" file with the same name tag and generates 3D unstructured VTU file.

# Keywords

  * `gridType::Symbol`: Type of target VTK grid (vti: image, vtr: rectilinear, vts: structured grid).
