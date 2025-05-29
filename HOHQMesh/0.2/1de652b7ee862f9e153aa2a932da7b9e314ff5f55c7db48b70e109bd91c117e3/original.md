```
generate_mesh(proj::Project; verbose=false, subdivision_maximum=8)
```

Generate a mesh from the information stored in a `Project` created using the interactive mesh functionality. First a check is made if a background grid exists and all inner/outer boundary curves are valid.

This function will then make a HOHQMesh control file from the control dictionary `proj.controlDict` and use it to call the wrapper function that interfaces with HOHQMesh. The resulting mesh and control files will be saved to `proj.projectDirectory`. Also, if there is an active plot of the mesh project it will update to display the generated mesh.

With the optional argument `verbose` one can activate verbose output from HOHQMesh that prints additional messages and debugging mesh information.

To override the maximum number of allowable subdivisions in the quad tree during meshing adjust the value of `subdivision_maximum`. The default value of `subdivision_maximum` is 8, meaning that elements can be up to a factor of `2^8` smaller than the background grid. Note, think before doing this! It could be adjusting the boundary curves, background grid size, adding local refinement regions, or some combination may remove the need to adjust the subdivision depth.

This function returns the output to `stdout` of the HOHQMesh binary when generating the mesh.
