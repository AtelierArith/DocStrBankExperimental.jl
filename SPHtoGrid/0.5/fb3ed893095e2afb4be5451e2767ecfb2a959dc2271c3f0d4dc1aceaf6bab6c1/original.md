```
distributed_allsky_map( allsky_filename::String, 
                        Nside::Integer, Nsubfiles::Integer, 
                        mapping_function::Function;
                        reduce_image::Bool=true)
```

Dynamically dispatches workers to compute one allsky map per subfile, sum up the results and save to a fits file.

# Arguments

  * `allsky_filename::String`: Name of the file under which the image should be saved
  * `Nside::Integer`: `Nside` for healpix map, must be a power of 2! `Nside = 2^N`.
  * `Nsubfiles::Integer`: Number of subfiles the snapshot is distributed over.
  * `mapping_function::Function`: The function to be executed per subfile. Must have a call to [`allsky_map`](@ref) as return value.
  * `reduce_image`: If the final image should be divided by the weight image set to `true`
