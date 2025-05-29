```
HDF5Logger
```

Creates an object for logging frames of data to an HDF5 file. The frames are expected to have the same size, and the total number of frames to log is expected to be known in advance. It currently works with scalars, vectors, and matrices of basic types that the HDF5 package supports.

# Example 1: Logging a Vector over Time

```julia
log = Log("my_file.h5") # Create a logger.
num_frames = 100        # Set the total number of frames to log.
example_data = [1., 2., 3.] # Create an example of a frame of data.
add!(log, "/a_vector", example_data, num_frames) # Create the stream.
log!(log, "/a_vector", [4., 5., 6.]) # Log a single frame of data.
log!(log, "/a_vector", [7., 8., 9.]) # Log the next frame.
close!(log) # Always clean up when done. Use try-catch to make sure.

# Read it back out using the regular HDF5 library.
using HDF5
x = HDF5.h5open("my_file.h5", "r") do logs
    read(logs, "/a_vector")
end
```

# Example 2: Logging a Scalar over Time

The underlying HDF5 library (HDF5.jl) logs things as arrays, so passing in scalars will result in 1-by-n arrays in the HDF5 file, instead of an n-length Vector. One can retrieve the n-length Vector by using `squeeze`. E.g.:

```julia
log = Log("my_file.h5") # Create a logger.
add!(log, "/a_scalar", 0., 1000) # Create stream with space for 1000 samples.
log!(log, "/a_scalar", 0.1) # Log a single frame of data.
log!(log, "/a_scalar", 0.2) # Log the next frame.
close!(log) # Always clean up when done. Use try-catch to make sure.

# Read it back out using the regular HDF5 library.
using HDF5
t = HDF5.h5open("my_file.h5", "r") do logs
    read(logs, "/a_scalar")
end # t is now a 1-by-1000 Array.
t = squeeze(t, 1) # Make an n-element Vector.
```

# Notes

One often needs to `log!` immediately after an `add!`, so the `add!` function can also log its example data as the first frame for convenience. Just use:

```julia
add!(log, "/group/name", data, num_frames, true) # Add stream; log data.
```
