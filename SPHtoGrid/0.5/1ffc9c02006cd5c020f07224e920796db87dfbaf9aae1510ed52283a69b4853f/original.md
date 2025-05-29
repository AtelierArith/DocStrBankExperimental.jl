```
distributed_cic_map(cic_filename::String, Nsubfiles::Integer,
                    mapping_function::Function,
                    Nimages::Integer, param::mappingParameters;
                    reduce_image::Bool=true,
                    Ndim::Integer=2,
                    snap::Integer=0,
                    units::String="",
                    vtk::Bool=true)
```

Dynamically dispatches workers to compute one cic map per subfile, sum up the results and save to a fits file.

# Arguments

  * `cic_filename::String`: Name of the file under which the image should be saved
  * `Nsubfiles::Integer`: Number of subfiles the snapshot is distributed over.
  * `mapping_function::Function`: The function to be executed per subfile. Must return a `Tuple` of the cic image(s) and the weight_image.
  * `Nimages::Integer=1`: Number of cic image that are constructed simultaniously. Only useful if you map multiple quantities at once, so it defaults to `1`.
  * `param::mappingParameters`: Parameters for the mapping, needed to save the image in the usual way.
  * `reduce_image`: If the final image should be divided by the weight image set to `true`.
  * `Ndim::Integer=2`: Dimensions of image, must be either `2` or `3`.
  * `snap::Integer=0`: Number of the input snapshot, used for saving the image.
  * `units::String=""`: Units of the image, used for saving the image.
